# Zero Trust RAG Architecture - Overview

Costa Rica

[![GitHub](https://img.shields.io/badge/--181717?logo=github&logoColor=ffffff)](https://github.com/)
[Cloud2BR OSS - Learning Hub](https://github.com/Cloud2BR-MSFTLearningHub)

Last updated: 2026-04-06

----------

> For Azure AI Search and OpenAI in a Retrieval-Augmented Generation (RAG) setup, find below an example of how these components are interconnected within a secure Azure environment.

<details>
<summary><b> References </b> (Click to expand)</summary>
   
- [RAG Microsoft Enterprise RAG Solution Accelerator (GPT-RAG) - github repo](https://github.com/Azure/GPT-RAG)
- [Overview – Apply Zero Trust principles to Azure IaaS](https://learn.microsoft.com/en-us/security/zero-trust/azure-infrastructure-overview)
- [Zero Trust defined](https://www.microsoft.com/en-us/security/business/zero-trust?msockid=38ec3806873362243e122ce086486339)
- [Zero Trust Essentials eBook](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/zero-trust-essentials-ebook.pdf)
  
</details>

## Overview

> Zero Trust AI architecture in Microsoft Azure is a `security framework designed to protect data, applications, and infrastructure by assuming that threats can come from both inside and outside the network`. This model operates on the principle of "never trust, always verify", meaning `every access request is thoroughly authenticated and authorized based on all available data points, regardless of its origin. The architecture integrates multiple layers of security, including strong identity verification, device compliance checks, and least privilege access, ensuring that only authorized users and devices can access sensitive resources`. By continuously monitoring and validating each request, Zero Trust AI architecture helps organizations minimize risks and enhance their overall security posture. As Microsoft defined Zero Trust:

<div align="center">
  <img width="800" alt="image" src="https://github.com/user-attachments/assets/1736d8bd-cb75-497d-8b0a-71e8d5344c9f" style="border: 2px solid #4CAF50; border-radius: 5px; padding: 5px;"/>
</div>

From [Microsoft Security](https://www.microsoft.com/en-us/security/business/zero-trust?msockid=38ec3806873362243e122ce086486339)

## Components

1. **Azure Services Subscription**: The overarching subscription under which all services are organized.
2. **Resource Group (RG) for RAG**: A logical container that holds related resources, ensuring they are managed and secured together.
3. **Storage Account**: Used to store data securely.
4. **AI + Machine Learning Services**: This includes:
   - **Azure AI Search**: For indexing and searching documents.
   - **Azure OpenAI**: For generating responses based on retrieved documents.
   - **Azure Key Vault**: For securely storing secrets like API keys and connection strings.
5. **Virtual Network (VNet)**: Provides network isolation and security. It contains subnets such as:
   - **AI-services-subnet**: Hosts AI-related services.
   - **app-service-subnet**: Hosts application services.
6. **VM for Data Science**: A virtual machine used for data science tasks within the AI-services-subnet.
7. **App Service Plan and Web App**: Part of the app-service-subnet, used to host web applications.

## Workflow in Zero Trust Architecture

> Network Interface & Network Security Groups: 

<div align="center">
  <img width="800" alt="image" src="https://github.com/user-attachments/assets/aa342b5d-76ed-4b1e-8ab6-18a1dbc19701" style="border: 2px solid #4CAF50; border-radius: 5px; padding: 5px;"/>
</div>

> Zero trust: Initial Phase

<div align="center">
  <img width="800" alt="image" src="https://github.com/user-attachments/assets/16f0ec13-83b6-4e12-8719-5282d7291758" style="border: 2px solid #4CAF50; border-radius: 5px; padding: 5px;"/>
</div>

> Microsoft Enterprise RAG Solution Accelerator: 

1. **User Interaction**: The user initiates a request from their device.
2. **Azure Front Door and WAF**: The request is routed through Azure Front Door and Web Application Firewall (WAF) for initial security checks.
3. **App Service (Frontend)**: The request reaches the frontend application hosted on Azure App Service via a private endpoint.
4. **Orchestrator (Azure Function)**: The frontend communicates with an orchestrator function within the VNet, which manages the flow of data.
5. **Database Access**: The orchestrator accesses Azure Cosmos DB to retrieve conversation history.
6. **Vector Embedding**: The orchestrator requests Azure OpenAI to generate vector embeddings from the user’s query.
7. **Key Vault Access**: The orchestrator retrieves the AI Search API key from Azure Key Vault.
8. **Document Retrieval**: The orchestrator queries Azure AI Search to retrieve relevant documents.
9. **Response Generation**: The orchestrator uses Azure OpenAI to generate a response based on the retrieved documents.
10. **Response Delivery**: The response is sent back to the user through the same secure path.

<div align="center">
  <img width="800" alt="image" src="https://github.com/user-attachments/assets/8246a0cd-622a-4d1e-b575-08123e9b3458" style="border: 2px solid #4CAF50; border-radius: 5px; padding: 5px;"/>
</div>

From [Zero Trust Architecture Deployment](https://github.com/Azure/GPT-RAG?tab=readme-ov-file#zero-trust-architecture-deployment)

<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1309-limegreen" alt="Total views">
  <p>Refresh Date: 2026-07-01</p>
</div>
<!-- END BADGE -->
