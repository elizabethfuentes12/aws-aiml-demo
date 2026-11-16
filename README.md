# Servicios de AI-ML y generative AI en AWS: Demos para aprender en un Jupyter Notebook.

----

![Diagram translator chatbot app"](images/portada.png)


🇻🇪🇨🇱 [Dev.to](https://dev.to/elizabethfuentes12) [Linkedin](https://www.linkedin.com/in/lizfue/) [GitHub](https://github.com/elizabethfuentes12/) [Twitter](https://twitter.com/elizabethfue12) [Instagram](https://www.instagram.com/elifue.tech) [Youtube](https://www.youtube.com/channel/UCr0Gnc-t30m4xyrvsQpNp2Q)
[Linktr](https://linktr.ee/elizabethfuentesleone)

> 💰 **Nota:** Algunos servicios estan en la capa gratuita y otros no, asegurate de revisar los valores involucrados antes de empezar --> [Link](https://aws.amazon.com/es/free/?all-free-tier.sort-by=item.additionalFields.SortRank&all-free-tier.sort-order=asc&awsf.Free%20Tier%20Types=*all&awsf.Free%20Tier%20Categories=*all)

> 👷🏻‍♀️ **Configuración de la cuenta AWS:** Todas las demos se ejecutan en un jypiter notebook, por lo que debes tener configurado la cuenta de AWS en tu computador o ambiente, sigue los pasos aca --> [Link](https://docs.aws.amazon.com/es_es/cli/latest/userguide/cli-configure-files.html#:~:text=export%20AWS_PROFILE%3Duser1-,Definir%20y%20ver%20las%20opciones%20de%20configuraci%C3%B3n%20mediante%20comandos,-Hay%20varias%20formas)

## Empieza creando el ambiente

```
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

> 🔄 **Actualización noviembre 2026.** Amazon Titan Text, Anthropic Claude 3.x (incluido Claude 3.5 Sonnet) y Stable Diffusion XL llegaron a su fin de vida en Amazon Bedrock ([Model lifecycle](https://docs.aws.amazon.com/bedrock/latest/userguide/model-lifecycle.html)). Los notebooks de Bedrock se migraron y se ejecutaron completos contra Bedrock en `us-east-1` (`boto3 1.44.3`, `langchain-aws 1.9.3`).
>
> | Antes (EOL) | Ahora | Cómo se invoca | Doc |
> |---|---|---|---|
> | `amazon.titan-tg1-large`, `amazon.titan-text-premier-v1:0` | `us.amazon.nova-2-lite-v1:0` | Converse / ConverseStream | [Nova 2 Lite](https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-nova-2-lite.html), [Converse API](https://docs.aws.amazon.com/bedrock/latest/userguide/conversation-inference-call.html) |
> | `anthropic.claude-3-haiku-20240307-v1:0`, `claude-instant-v1` | `global.anthropic.claude-haiku-5-5` | Converse o Messages API (InvokeModel) | [Claude Haiku 5.5](https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-haiku-5-5.html) |
> | `anthropic.claude-3-sonnet-20240229-v1:0` | `global.anthropic.claude-sonnet-5-5` | Messages API (InvokeModel) | [Claude Sonnet 5.5](https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-anthropic-claude-sonnet-5-5.html) |
> | `stability.stable-diffusion-xl-v1` | `stability.sd3-5-large-v1:0` (solo `us-west-2`) | InvokeModel | [SD 3.5 Large](https://docs.aws.amazon.com/bedrock/latest/userguide/model-parameters-diffusion-3-5-large.html) |
> | `amazon.titan-embed-g1-text-02` | sin cambio (sigue **Active**) | InvokeModel | [Titan Embeddings G1](https://docs.aws.amazon.com/bedrock/latest/userguide/model-card-amazon-titan-embeddings-g1---text.html) |
>
> Dos cambios de comportamiento de Claude 5.5 que afectan al código: ya no acepta `temperature`, `top_p` ni `top_k` (devuelve 400), y tiene [adaptive thinking](https://platform.claude.com/docs/en/build-with-claude/thinking) activado por defecto, así que la respuesta puede traer un bloque `thinking`/`reasoningContent` antes del texto. Los notebooks leen solo los bloques de texto y, en los ejemplos cortos, apagan el thinking (`"disabled"` en Haiku 5.5, `"between_tools"` en Sonnet 5.5). Detalles en la nota al inicio de cada notebook.
----
## [Generative AI al alcance de una llamada de API 🚀](https://github.com/elizabethfuentes12/aws-aiml-demo/tree/main/notebooks/amazon-bedrock-demo)
En estos notebook podrás utilizar la magia del Genai desde un par de lineas de comando gracias al poder de [Amazon Bedrock](https://aws.amazon.com/es/bedrock/). 

## [Generative AI: Introducción a prompt engineering 🚀](https://github.com/elizabethfuentes12/aws-aiml-demo/tree/main/notebooks/prompt-engineering-best-practices)

Con un prompt bien diseñado, las capacidades previamente entrenadas del modelo pueden aprovecharse para atender consultas novedosas dentro de su ámbito de aplicación. 

Aprende como [aca](https://github.com/elizabethfuentes12/aws-aiml-demo/tree/main/notebooks/prompt-engineering-best-practices)

## [Código de WorkShop 🧱 Construyendo con Amazon Bedrock y LangChain](https://catalog.workshops.aws/building-with-bedrock-and-langchain/es-US)

Descarga el código aca: 

```
curl 'https://static.us-east-1.prod.workshops.aws/public/78167ddb-3840-45eb-b24d-20b3a410f64a/assets/workshop.zip' --output workshop.zip
unzip workshop.zip
```

Sigue los pasos aca: [🧱 Construyendo con Amazon Bedrock y LangChain](https://catalog.workshops.aws/building-with-bedrock-and-langchain/es-US)

[Encuentra más workshops para aprender](https://workshops.aws/card/amazon%20bedrock)

## Notebooks prácticos para aprender a usar algunos de los [servicios de AIML de AWS](https://aws.amazon.com/machine-learning/)

### [Detectar entidades y sentimientos en un documento 🔎 📄](https://github.com/elizabethfuentes12/aws-aiml-demo/blob/main/notebooks/detecting-entities-and-sentiment-from-a-document.ipynb):
En este notebook podrás extraer texto de una imagen, identificar los sentimientos  y además las identidades mencionadas en el texto. 

### [¡Polly habla¡ 🦜](https://github.com/elizabethfuentes12/aws-aiml-demo/blob/main/notebooks/amazon_translate_polly.ipynb):
En este notebook podrás identificar el idioma de un trexto ingresado, traducirlo a otro idioma y repoducir un audio con la pronunciación del idioma destino. 

### [Genera subtítulos a un video y traducelos a otro idioma ⏯️ 🍿.](https://github.com/elizabethfuentes12/aws-aiml-demo/blob/main/notebooks/crea_subtitulos.ipynb)
En este notebook aprenderás a extraer subitulos de un video y a generar unos nuevos en otro idioma. 

### [Moderador de contenidos de video ⏯️ 🔫.](https://github.com/elizabethfuentes12/aws-aiml-demo/blob/main/notebooks/moderador_contenido.ipynb)
En este notebook aprenderas a crear un moderador de contenido de video.

### [Avanzado: Crea un recomendador de Anime](https://aws.amazon.com/es/blogs/aws-spanish/como-crear-un-modelo-de-recomendacion-basado-en-machine-learning/)
Esta es una serie blog donde te guio a crear una aplicación de recomendaciones de Anime, empleando un servicio permite a los desarrolladores crear y desplegar rápidamente recomendaciones curadas y segmentación de usuarios inteligente a escala mediante machine learning (ML).. sin ser especialista en ML. 

----

## 🚨¿Te gusto? 👩🏻‍💻 ¿Tienes comentarios?🎤 cuéntamelo todo --> [acá](https://www.pulse.aws/survey/WC6WAFGM)

----

## ¡Gracias!

Te dejo mis redes: 
🇻🇪🇨🇱 [Dev.to](https://dev.to/elizabethfuentes12) [Linkedin](https://www.linkedin.com/in/lizfue/) [GitHub](https://github.com/elizabethfuentes12/) [Twitter](https://twitter.com/elizabethfue12) [Instagram](https://www.instagram.com/elifue.tech) [Youtube](https://www.youtube.com/channel/UCr0Gnc-t30m4xyrvsQpNp2Q)
[Linktr](https://linktr.ee/elizabethfuentesleone)

---

## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.
