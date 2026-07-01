# Demonstration: Azure Open AI \& AI Foundry Pricing 

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
- [Azure OpenAI Service pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/openai-service/?msockid=38ec3806873362243e122ce086486339#pricing)
- [Plan to manage costs for Azure OpenAI Service](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/manage-costs)

</details>

<details>
<summary><b>Table of Content </b> (Click to expand)</summary>

- [Pricing Models](#pricing-models)
- [Pay-As-You-Go Price Calculation](#pay-as-you-go-price-calculation)
- [PTUs and TPM relationship](#ptus-and-tpm-relationship)
- [Provisioned PTU Capacity Calculator](#provisioned-ptu-capacity-calculator)

</details>

## Pricing Models 

Azure OpenAI Service supports different pricing models, including: 

- Standard (On-Demand): Pay only for the tokens processed. 
- Provisioned Throughput Units (PTUs): Ensure consistent throughput and minimal latency variance for scalable solutions. Click here to read more about [What is provisioned throughput?](https://learn.microsoft.com/en-us/azure/ai-services/openai/concepts/provisioned-throughput?tabs=global-ptum) 
- Batch API: For global deployments and some regions, providing completions within 24 hours at a 50% discount on Global Standard Pricing. Click to read more about [Getting started with Azure OpenAI batch deployments](https://learn.microsoft.com/en-us/azure/ai-services/openai/how-to/batch?tabs=global-batch%2Cstandard-input%2Cpython-secure&pivots=ai-foundry-portal)

| Billing Model | Description | Cost Calculation | Use Cases |
|------------------------------|---------------------|-----------------|----------------------------------------------|
| Pay-As-You-Go                | - Charged based on the number of tokens processed<br/>- Suitable for variable or unpredictable usage patterns| - Cost per unit of tokens, different rates for different model series<br/>- Includes both input and output tokens| - Applications with variable or unpredictable usage patterns<br/>- Flexibility in usage|
| Provisioned Throughput Units | - Reserved processing capacity for deployments<br/>- Ensures predictable performance and cost<br/>- **Reserved Capacity:** PTU provides reserved processing capacity for your deployments, ensuring predictable performance and cost.<br/>- **Capacity Planning:** It's important to estimate the required PTUs for your workload to optimize performance and cost. The token totals are calculated using the equation below. Click [here for more explanation on how to calculate it](#ptus-and-tpm-relationship) | - Hourly rate based on the number of PTUs deployed<br/>- Regardless of the number of tokens processed                                                                                                                                                   | - Well-defined, predictable throughput requirements<br/>- Consistent traffic<br/>- Real-time or latency-sensitive applications<br/>- **Cost Predictability:** PTU offers more predictable costs compared to the pay-as-you-go model, which can vary based on usage.<br/>- **Performance Guarantees:** PTU provides guaranteed throughput and latency constraints. |
| Batch API                    | - Designed for asynchronous, large-scale batch processing<br/>- Processes multiple requests in a single file rather than individually<br/>- Offers a 24-hour turnaround<br/>- Available with global deployments in select regions, achieving up to a 50% discount on Global Standard Pricing | - Calculated based on token usage (similar to Pay-As-You-Go) but incorporates a fixed discount (typically 50%) relative to standard pricing<br/>- Uses an independent enqueued token quota to ensure online workloads remain unaffected | - Ideal for non-real-time, high-volume tasks such as bulk content generation, data processing, document summarization, translation, or sentiment analysis<br/>- Effective when processing delay is acceptable in exchange for significant cost savings and throughput optimization |

> PTU Capacity Planning:

  $$
  \text{Total Tokens per Minute} = \text{Peak Calls per Minute} \times \Bigl( \text{Tokens in Prompt} + \text{Tokens in Response} \Bigr)
  $$

## Pay-As-You-Go Price Calculation

> The Pay-As-You-Go model `charges solely based on the cumulative number of tokens processed`. To accurately estimate your costs, first determine the total tokens processed per call by adding the tokens from both the prompt and the response. Then, scale that figure by your total number of calls over your desired period.

> [!NOTE]
>
> - Adjust the token counts and cost rate according to the specific model series or deployment region, as pricing may vary. <br/>
> - For the most up-to-date cost details and additional pricing factors, please review the [Azure Pricing Calculator](https://azure.microsoft.com/en-us/pricing/calculator/) and [Azure OpenAI Service pricing](https://azure.microsoft.com/en-us/pricing/details/cognitive-services/openai-service/?msockid=38ec3806873362243e122ce086486339#pricing) page.

> **Calculation Formula:**

$$
\text{Cost per Call} = \left(\frac{\text{Tokens in Prompt} + \text{Tokens in Response}}{1000}\right) \times \text{Cost per 1,000 Tokens}
$$

For instance, if each call processes 150 tokens (e.g., 50 tokens in the prompt and 100 tokens in the response) and the rate is defined as **X** per 1,000 tokens, then the cost for one call becomes:

$$
\text{Cost per Call} = \frac{150}{1000} \times X
$$

For multiple calls, simply multiply the cost per call by the total number of API calls:

$$
\text{Total Cost} = N \times \left(\frac{\text{Tokens in Prompt} + \text{Tokens in Response}}{1000}\right) \times \text{Cost per 1,000 Tokens}
$$

> Find below some examples:

<details>
<summary><strong>Definitions</strong></summary>

- **Use Case**: The scenario being measured (e.g., Small Chatbot Interaction, Enterprise QA Assistant, Bulk Content Generation).
- **Model**: The optional model choice (e.g., GPT‑3.5‑turbo, GPT‑4 with 8K/32K context) based on your needs.
- **Daily Count**: Number of interactions or API calls `per day.`
- **Avg Input Tokens**: Average tokens in the prompt `per interaction.`
- **Avg Output Tokens**: Average tokens in the completion `per interaction.`
- **Daily Input Tokens**: Daily Count × Avg Input Tokens.
- **Daily Output Tokens**: Daily Count × Avg Output Tokens.
- **Daily Total Tokens**: Sum of daily input and output tokens.
- **Monthly Input Tokens**: Daily Input Tokens × 30.
- **Monthly Output Tokens**: Daily Output Tokens × 30.
- **Monthly Total Tokens**: Sum of monthly input and output tokens.

</details>

| **Use Case**                | **Model (Optional)** | **Daily Count** | **Avg Input Tokens** | **Avg Output Tokens** | **Daily Input Tokens** | **Daily Output Tokens** | **Daily Total Tokens** | **Monthly Input Tokens** | **Monthly Output Tokens** | **Monthly Total Tokens** |
|-----------------------------|---------------------------------------------------------------------------|-----------------|----------------------|-----------------------|------------------------|-------------------------|------------------------|--------------------------|---------------------------|--------------------------|
| **Small Chatbot Interaction**   | (e.g., GPT‑3.5‑turbo or GPT‑4)                                           | 200             | 50                   | 150                   | 200 × 50 = 10,000      | 200 × 150 = 30,000      | 10,000 + 30,000 = 40,000| 10,000 × 30 = 300,000    | 30,000 × 30 = 900,000     | ~1,200,000               |
| **Enterprise QA Assistant**     | (e.g., GPT‑4 with 8K or 32K context depending on precision needs)        | 500             | 100                  | 300                   | 500 × 100 = 50,000     | 500 × 300 = 150,000     | 50,000 + 150,000 = 200,000 | 50,000 × 30 = 1,500,000  | 150,000 × 30 = 4,500,000   | ~6,000,000                |
| **Bulk Content Generation**     | (e.g., GPT‑3.5‑turbo or another efficient variant)                        | 2,000           | 100                  | 150                   | 2,000 × 100 = 200,000  | 2,000 × 150 = 300,000   | 200,000 + 300,000 = 500,000 | 200,000 × 30 = 6,000,000 | 300,000 × 30 = 9,000,000  | ~15,000,000              |

<https://github.com/user-attachments/assets/9ede2347-faaf-42c7-8e4c-64ad7c461938>

## PTUs and TPM relationship

> Provisioned Throughput Units (PTUs) <br/>
> Tokens Per Minute (TPM)

E.g 

| **PTUs** | **Calls per Minute** | **Tokens in Prompt** | **Tokens in Response** | **Tokens per Minute (TPM)** |
|----------|----------------------|----------------------|------------------------|-----------------------------|
| 1        | 10                   | 50                   | 100                    | 1,500                       |
| 2        | 20                   | 50                   | 100                    | 3,000                       |
| 5        | 50                   | 50                   | 100                    | 7,500                       |
| 10       | 100                  | 50                   | 100                    | 15,000                      |
| 20       | 200                  | 50                   | 100                    | 30,000                      |
| 50       | 500                  | 50                   | 100                    | 75,000                      |

> Explanation:

- **PTUs**: Provisioned Throughput Units represent the capacity of tokens that can be processed per minute.
- **Calls per Minute**: The number of API calls that can be made per minute.
- **Tokens in Prompt**: The number of tokens in the input prompt for each call.
- **Tokens in Response**: The number of tokens in the model's response for each call.
- **Tokens per Minute (TPM)**: The total number of tokens processed per minute, calculated as:

$$
\text{TPM} = \text{Calls per Minute} \times (\text{Tokens in Prompt} + \text{Tokens in Response})
$$

> Example Calculation:
For 50 PTUs:

1. **Calls per Minute**: Calculate the number of calls per minute:

$$
\text{Calls per Minute} = \text{PTUs} \times \text{Calls per PTU per Minute}
$$

$$
\text{Calls per Minute} = 50 \times 10 = 500
$$

2. **Tokens per Minute**: Calculate the total tokens per minute:

$$
\text{TPM} = \text{Calls per Minute} \times (\text{Tokens in Prompt} + \text{Tokens in Response})
$$

$$
\text{TPM} = 500 \times (50 + 100) = 500 \times 150 = 75,000
$$

This means with 50 PTUs, you can process 75,000 tokens per minute.

## Provisioned (PTU) Capacity Calculator

> Improve accuracy of your estimate by adding multiple workloads to your PTU calculation. Each workload will be calculated and displayed as well as the aggregate total if both are running at the same time to your deployment.

<img width="750" alt="image" src="https://github.com/user-attachments/assets/d7599273-b4e3-478a-b2b0-b72f8647bb0e" />

<img width="750" alt="image" src="https://github.com/user-attachments/assets/540a1fd2-cae1-445c-8ca8-a0123cc63d7e" />

<https://github.com/user-attachments/assets/27beba15-57d6-4a2b-943e-496829644dbe>

<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1309-limegreen" alt="Total views">
  <p>Refresh Date: 2026-07-01</p>
</div>
<!-- END BADGE -->
