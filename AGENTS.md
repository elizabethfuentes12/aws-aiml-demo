# AGENTS.md — aws-aiml-demo

Jupyter notebooks (in Spanish, some in English) that teach AWS AI/ML services and generative AI with Amazon Bedrock: text generation, code generation, summarization, Q&A, entity extraction, prompt engineering, plus Comprehend/Polly/Transcribe/Rekognition/Textract demos.

## Structure

```
README.md                                   # index of all demos (Spanish)
requirements.txt                            # boto3, langchain-aws, bs4, pillow, matplotlib
notebooks/
  amazon-bedrock-demo/
    00_Prerequisites/bedrock_basics.ipynb              # Converse (Nova 2 Lite), Messages API (Claude Haiku 5.5), SD 3.5 Large, Titan Embeddings G1
    00_Prerequisites/Getting_started_with_Converse_API.ipynb
    01_Text_generation/00..04_*.ipynb                  # Nova 2 Lite via Converse; Claude Sonnet 5.5 via InvokeModel; LangChain ChatBedrockConverse
  prompt-engineering-best-practices/*.ipynb            # Converse with Claude Haiku 5.5 (Spanish)
  amazon_translate_polly.ipynb, crea_subtitulos.ipynb, detecting-entities-and-sentiment-from-a-document.ipynb, moderador_contenido.ipynb
play_ground.ipynb / play_ground.py          # scratch
```

## Run

```bash
python3 -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt
# AWS credentials with Bedrock model access in us-east-1 (SD 3.5 Large is called in us-west-2)
```
Open the notebooks in JupyterLab or VS Code. Headless check used for the November 2026 update:
`jupyter nbconvert --to notebook --execute <nb> --ExecutePreprocessor.timeout=600` from the notebook's own directory (01_Text_generation notebooks read `emails/` and write `sales.csv`, which is a runtime artifact and is not committed).

## Models and APIs (verified live, November 2026)

| Purpose | Model ID | API |
|---|---|---|
| Text generation (Titan replacement) | `us.amazon.nova-2-lite-v1:0` | `converse` / `converse_stream` |
| Fast Claude | `global.anthropic.claude-haiku-5-5` | Converse or InvokeModel (Messages API) |
| Code generation / summarization | `global.anthropic.claude-sonnet-5-5` | InvokeModel (Messages API) |
| Image generation | `stability.sd3-5-large-v1:0` | InvokeModel, `region_name="us-west-2"` |
| Embeddings | `amazon.titan-embed-g1-text-02` | InvokeModel (still Active) |

## Gotchas (all hit during the live run)

- Claude 4.7+ rejects `temperature`, `top_p`, `top_k` (HTTP 400) on both InvokeModel and Converse. Do not add them back.
- Claude 5.5 has adaptive thinking on by default: responses start with a `thinking` (Invoke) / `reasoningContent` (Converse) block. Never read `content[0]["text"]`; filter blocks with `"text" in block` / `type == "text"`, or `AIMessage.text` in LangChain. Streaming: only `delta.type == "text_delta"` (Invoke) or deltas that contain `text` (Converse).
- With a small token budget Claude can spend everything on thinking and return no text. Haiku 5.5 accepts `"thinking": {"type": "disabled"}`; Sonnet 5.5 rejects `disabled` and needs `{"type": "between_tools"}`. Nova does not accept a `thinking` field at all, so model-agnostic helpers (Converse notebook) do not send it.
- Nova 2 Lite must be called through an inference profile (`us.` / `global.` prefix), not the bare model ID.
- `amazon.titan-tg1-large`, `titan-text-premier`, Claude 3.x, Claude Instant and SDXL return `ResourceNotFoundException: This model version has reached the end of its life`.

## Conventions

- Keep the EOL/update note at the top of each Bedrock notebook and link official docs for every API shape; do not write request bodies from memory.
- Commit notebooks with fresh outputs except for `%pip install` cells and the SD 3.5 image cell (kept empty to keep the repo small).
- Non-Bedrock notebooks (Comprehend, Polly, Transcribe, Rekognition) need user-owned S3 buckets (`s3://TU-CUENTA/...`) and were not changed in this update.

## Recent changes

- 2026-11-16: migrated the 9 Bedrock notebooks off EOL models (Titan Text, Claude 3.x, SDXL) to Nova 2 Lite, Claude Haiku/Sonnet 5.5 and SD 3.5 Large; moved Titan calls to the Converse API; `ChatBedrock` → `ChatBedrockConverse`; removed the unused `anthropic` dependency and the stray `FETCH_HEAD` file; all 9 notebooks executed end to end with zero error cells.
