# [Amazon Bedrock](https://aws.amazon.com/es/bedrock/): Genai al alcance de una llamada de API. 

## Información general

Amazon Bedrock es un servicio totalmente administrado que permite que los modelos fundacionales (FM) de las principales startups de IA estén disponibles a través de una API, de modo que puede elegir entre varios modelos fundacionales para encontrar el que mejor se adapte a su caso de uso. Con la experiencia sin servidor de Amazon Bedrock, puede comenzar rápidamente, experimentar fácilmente con los modelos fundacionales, personalizarlos de forma privada con sus propios datos e integrarlos e implementarlos sin problemas en sus aplicaciones mediante las herramientas y capacidades de AWS. Los agentes para Amazon Bedrock están totalmente administrados y facilitan a los desarrolladores la creación de aplicaciones de inteligencia artificial generativa que pueden ofrecer respuestas actualizadas basadas en fuentes de conocimiento propias y completar tareas para una amplia gama de casos de uso.

> **Nota:** antes de empezar revisa su valor --> [Amazon Bedrock pricing](https://aws.amazon.com/es/bedrock/pricing/).

![Architecture](https://community.aws/_next/image?url=https%3A%2F%2Fcommunity.aws%2Fraw-post-images%2Fposts%2Fworking-with-your-live-data-using-langchain%2Fimages%2Ffig_01.png&w=1920&q=75)

## Antes de empezar debes configurarlo en la consola. 

### Crea una Cuenta gratuita

- [Crear cuenta](https://aws.amazon.com/es/free/)

> **Nota:** AWS tiene una capa gratuita para varios de sus servicios, revisa cuales estan dentro de esa capa gratiuta [aca](https://aws.amazon.com/es/free/). Ten en cuenta que [Amazon Bedrock](https://aws.amazon.com/es/bedrock/pricing/) no esta dentro de esa capa gratuita.

### Ingresa a la consola

![Architecture](imagenes/bedrock_1.gif)

### Accede a los modelos

![Architecture](imagenes/bedrock_2.gif)

### Listo para utilizar!

![Architecture](imagenes/bedrock_3.gif)

### Como usar Amazon Bedrock como una llamada de API empleando el [AWS SDK para Python](https://aws.amazon.com/es/sdk-for-python/).

- Instala la libreria de Boto3.

```python
pip install boto3  
``` 
- Aprende más de las [API con boto3](https://boto3.amazonaws.com/v1/documentation/api/latest/guide/resources.html). 

- Instala la AWS Linea de Comandos (CLI) en tu computador. 

Sigue los pasos en [este link](https://aws.amazon.com/es/cli/). 

## Algunos enlaces para que pueda seguir aprendiendo y desarrollando:

- [Integrating Foundation Models into Your Code with Amazon Bedrock](https://www.youtube.com/watch?v=ab1mbj0acDo)

- [Amazon Bedrock Workshop](https://github.com/aws-samples/amazon-bedrock-workshop)

- [AWS Kendra LangChain Extensions](https://github.com/aws-samples/amazon-kendra-langchain-extensions/tree/main)

- [Prompt Engineering Techniques](https://www.promptingguide.ai/techniques)

- [Learn the fundamentals of generative AI for real-world applications](https://www.deeplearning.ai/courses/generative-ai-with-llms/)

- [LangChain for LLM Application Development](https://www.deeplearning.ai/short-courses/langchain-for-llm-application-development/)
