# Demonstration: Azure AI Search Pricing 

Costa Rica

[![GitHub](https://badgen.net/badge/icon/github?icon=github&label)](https://github.com) 
[![GitHub](https://img.shields.io/badge/--181717?logo=github&logoColor=ffffff)](https://github.com/)
[Cloud2BR OSS - Learning Hub](https://github.com/Cloud2BR-MSFTLearningHub)

Last updated: 2026-04-06

----------

> [!NOTE]
> Please note the last updated date, as the values shown in the video might change over time due to price adjustments.

<details>
<summary><b>List of References </b> (Click to expand)</summary>

- [Azure Pricing Calculator](https://azure.microsoft.com/en-us/pricing/calculator/)
- [Azure AI Search pricing](https://azure.microsoft.com/en-us/pricing/details/search/?msockid=38ec3806873362243e122ce086486339)

</details>

> Priced based on a capacity-based model using Search Units (SUs), and charges vary depending on the tier and features you use. You are charged hourly based on the number of SUs, which are calculated as:

   $$
   \text{SUs} = \text{Replicas} \times \text{Partitions}
   $$

> E.g.1: Small Knowledge Base

- **Number of documents**: 2,000  
- **Pages per document**: 10  
- **Total pages**: 20,000  
- **Estimated index size**: ~ 200 MB  
- **Use case**: Internal company wiki with semantic search  
- **Suggested tier**: `Basic or Standard S1 with 1 replica, 1 partition`

> E.g.2: E-commerce Product Catalog

- **Number of products**: 50,000  
- **Attributes per product**: 15 (title, description, price, tags, etc.)  
- **Estimated index size**: ~ 1–2 GB  
- **Use case**: Product search with filters and semantic ranking  
- **Suggested tier**: `Standard S1 with 2 replicas, 1 partition (for high availability)`  

> E.g.3: Legal Document Archive

- **Number of documents**: 100,000  
- **Pages per document**: 25  
- **Total pages**: 2.5 million  
- **Estimated index size**: ~ 10–15 GB  
- **Use case**: Legal search with OCR, entity recognition, and semantic search  
- **Suggested tier**: `Standard S2 or Storage Optimized L1 with 2+ partitions`  

> E.g.4: News Aggregator

- **Articles per day**: 5,000  
- **Retention**: 1 year  
- **Total documents**: ~ 1.8 million  
- **Estimated index size**: ~ 8–10 GB  
- **Use case**: Real-time news search with filters and AI enrichment  
- **Suggested tier**: `Standard S2 or S3 with 3 replicas, 2 partitions`

<https://github.com/user-attachments/assets/809199a9-8a3f-4540-b4fa-d6358e685c01>

<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1309-limegreen" alt="Total views">
  <p>Refresh Date: 2026-07-01</p>
</div>
<!-- END BADGE -->
