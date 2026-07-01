# Retrieval-Augmented Generation (RAG) pattern - Overview 

Costa Rica

[![GitHub](https://img.shields.io/badge/--181717?logo=github&logoColor=ffffff)](https://github.com/)
[Cloud2BR OSS - Learning Hub](https://github.com/Cloud2BR-MSFTLearningHub)

Last updated: 2026-04-06

----------

<details>
<summary><b>List of References </b> (Click to expand)</summary>
   
- [What's Azure AI Search?](https://learn.microsoft.com/en-us/azure/search/search-what-is-azure-search)
- [Indexer overview - Azure AI Search](https://learn.microsoft.com/en-us/azure/search/search-indexer-overview)
- [Field mappings and transformations using Azure AI Search indexers](https://learn.microsoft.com/en-us/azure/search/search-indexer-field-mappings)
- [Azure AI Search Sample Data](https://github.com/Azure-Samples/azure-search-sample-data/tree/main)
- [Add scoring profiles to boost search scores](https://learn.microsoft.com/en-us/azure/search/index-add-scoring-profiles)
- [Relevance in keyword search (BM25 scoring)](https://learn.microsoft.com/en-us/azure/search/index-similarity-and-scoring)
- [Tips for better performance in Azure AI Search](https://learn.microsoft.com/en-us/azure/search/search-performance-tips)
- [Retrieval Augmented Generation (RAG) in Azure AI Search](https://learn.microsoft.com/en-us/azure/search/retrieval-augmented-generation-overview)
- [Service limits in Azure AI Search](https://learn.microsoft.com/en-us/azure/search/search-limits-quotas-capacity)
- [Semantic ranking in Azure AI Search](https://learn.microsoft.com/en-us/azure/search/semantic-search-overview)
- [Create a skillset in Azure AI Search](https://learn.microsoft.com/en-us/azure/search/cognitive-search-defining-skillset)
- [Skillset concepts in Azure AI Search](https://learn.microsoft.com/en-us/azure/search/cognitive-search-working-with-skillsets)
- [Custom AML skill in skillsets - Azure AI Search](https://learn.microsoft.com/en-us/azure/search/cognitive-search-aml-skill)
- [OCR skill - Azure AI Search](https://learn.microsoft.com/en-us/azure/search/cognitive-search-skill-ocr)
- [Custom Web API skill in skillsets - Azure AI Search](https://learn.microsoft.com/en-us/azure/search/cognitive-search-custom-skill-web-api)
- [Language detection cognitive skill - Azure AI Search](https://learn.microsoft.com/en-us/azure/search/cognitive-search-skill-language-detection)
- [Entity Recognition cognitive skill (v3) - Azure AI Search](https://learn.microsoft.com/en-us/azure/search/cognitive-search-skill-entity-recognition-v3)
- [Key Phrase Extraction cognitive skill - Azure AI Search](https://learn.microsoft.com/en-us/azure/search/cognitive-search-skill-keyphrases)
- [Image Analysis cognitive skill - Azure AI Search](https://learn.microsoft.com/en-us/azure/search/cognitive-search-skill-image-analysis)
- [Text split skill - Azure AI Search](https://learn.microsoft.com/en-us/azure/search/cognitive-search-skill-textsplit)
- [AI Search by sku limits/quota](https://learn.microsoft.com/en-us/azure/search/search-limits-quotas-capacity)

</details>

## Overview 

| **Step**       | **Definition** | **Implementation with Azure** |
|----------------|----------------|-------------------------------|
| **Retrieval**  | Retrieval involves searching and extracting relevant documents or data from a knowledge base or external data source based on the input query. | Use Azure AI Search to index and query documents stored in Azure Storage Blob Containers. Configure the search index to perform semantic search and return the most relevant results. |
| **Augmentation** | Augmentation involves enhancing the input query with the retrieved information to provide additional context and details. | Use Azure AI Search skillsets to preprocess the retrieved data, extracting key phrases, entities, and contextual information. This augmented input is then used to inform the generative model. |
| **Generation** | Generation involves using a generative model to process the augmented input and produce a coherent and contextually relevant response. | Deploy a generative model like GPT-4 on Azure OpenAI Service. Use an Azure Function App to orchestrate the data flow, calling the Azure OpenAI API to generate responses based on the augmented input. |

> Implementing RAG Pattern with Azure AI:

```mermaid
graph LR
    A[Set Up a Knowledge Base] --> B[Configure Retrieval System] --> C[Integrate with a GenModel]
```

1. **Set Up a Knowledge Base**: Store your documents in Azure Storage Blob Containers or another accessible data source.
2. **Configure a Retrieval System**: Use Azure AI Search to index and retrieve relevant documents based on user queries.
3. **Integrate with a Generative Model**: Use a generative model like GPT-4 to process the retrieved documents and generate responses.

> Traditional methods and the `Retrieval-Augmented Generation (RAG)` pattern:

| **Aspect**                | **Traditional Methods**| **RAG Pattern** |
|---------------------------|-------------------------------------|-----------------------------------------------------|
| **Model Type**            | Static, pre-trained models that rely on historical data. These models do not update dynamically and can become outdated. | Dynamic integration of retrieval and generative models, allowing for real-time data updates, keeping responses current and relevant. |
| **Data Freshness**        | Relies on pre-trained data, which may not reflect the latest information.                | Retrieves the most recent data from external sources, ensuring up-to-date information.            |
| **Context Understanding** | Often lacks the ability to fully understand the context of a query, leading to less accurate results. | Enhances context understanding by incorporating real-time information retrieval, providing richer context for responses. |
| **Retrieval Techniques**  | Uses keyword matching techniques like BM25 and TF-IDF, which may not capture the semantic meaning of queries. | Employs advanced semantic search techniques that better understand the intent behind queries, leading to more relevant results. |
| **Accuracy**              | May struggle with understanding context and semantic meaning, resulting in less accurate responses. | Improves accuracy by grounding responses in verified external knowledge, reducing the likelihood of errors. |
| **Risk of Hallucinations**| Higher risk of generating incorrect information as responses are based solely on training data. | Reduces this risk by grounding responses in real-time, verified information from external sources. |
| **Flexibility**           | Limited to specific data types and formats, which can restrict their applicability.      | Capable of handling various data types, including text, images, and videos, making it more versatile. |
| **Adaptability**          | Requires extensive retraining to incorporate new information, which can be time-consuming and costly. | More adaptable as it integrates real-time data without the need for frequent retraining.           |
| **Cost Efficiency**       | Can be resource-intensive due to the need for frequent retraining and large labeled datasets. | More cost-effective as it minimizes the need for extensive retraining and leverages existing data sources. |
| **Applications**          | Suitable for basic search and static content generation.                                | Ideal for complex applications such as healthcare, customer support, and content creation, where up-to-date and contextually relevant information is crucial. |

## Applications of RAG Pattern

```mermaid
 graph TD
    A[RAG Pattern]
    A --> B[Retrieval]
    B --> C[Knowledge Base]
    B --> D[External Data Source]
    A --> E[Augmentation]
    E --> F[Contextual Info]
    E --> G[Enhanced Query]
    A --> H[Generation]
    H --> I[LLM: e.g GPT-4]
    H --> J[Coherent Response]
    A --> K[Applications]
    K --> L[Question Answering]
    L --> M[Definition]
    L --> N[Implementation]
    K --> O[Document Summarization]
    O --> P[Definition]
    O --> Q[Implementation]
    K --> R[Conversational AI]
    R --> S[Definition]
    R --> T[Implementation] 
```

<details>
<summary><b>Question Answering</b></summary>

> Providing accurate answers by retrieving relevant documents and generating responses based on them.

- **Implementation**:
  - **Retrieval**:
    - Use Azure AI Search to index a large corpus of documents, such as research papers, articles, or FAQs.
    - Perform semantic search to retrieve the most relevant documents based on the query.
  - **Augmentation**: Extract key information from the retrieved documents using Azure AI Search skillsets (key phrase extraction, entity recognition, language detection).
  - **Generation**:
    - Use Azure OpenAI Service to generate a coherent and contextually relevant answer by processing the augmented input.
    - Orchestrate the data flow using Azure Function App.

</details>

<details>
<summary><b>Document Summarization</b></summary>

> Summarizing documents by retrieving key sections and generating concise summaries.

- **Implementation**:
  - **Retrieval**:
    - Use Azure AI Search to index documents such as reports, articles, and books.
    - Retrieve the most relevant sections of the document based on the summary request.
  - **Augmentation**: Identify key sentences, paragraphs, and sections using Azure AI Search skillsets.
  - **Generation**:
    - Use Azure OpenAI Service to generate a concise summary by processing the augmented input.
    - Orchestrate the data flow using Azure Function App.

</details>

<details>
<summary><b>Conversational AI</b></summary>

> Enhancing chatbot responses with up-to-date information from external sources.

- **Implementation**:
  - **Retrieval**:
    - Use Azure AI Search to index a knowledge base containing FAQs, support articles, and user manuals.
    - Retrieve the most relevant documents based on the conversation.
  - **Augmentation**: Extract key information from the retrieved documents using Azure AI Search skillsets (answers to common questions, troubleshooting steps, product details).
  - **Generation**:
    - Use Azure OpenAI Service to generate coherent and contextually relevant chatbot responses by processing the augmented input.
    - Orchestrate the data flow using Azure Function App.

</details>

<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1309-limegreen" alt="Total views">
  <p>Refresh Date: 2026-07-01</p>
</div>
<!-- END BADGE -->
