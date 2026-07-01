# Troubleshooting: Known Errors 

Costa Rica

[![GitHub](https://img.shields.io/badge/--181717?logo=github&logoColor=ffffff)](https://github.com/)
[Cloud2BR OSS - Learning Hub](https://github.com/Cloud2BR-MSFTLearningHub)

Last updated: 2026-04-06

------------------------------------------

<details>
<summary><b>Table of Content </b> (Click to expand)</summary>

- [Service Quota Exceeded](#service-quota-exceeded)

</details>

## Service Quota Exceeded

> The  deployment request is attempting to provision a service at a tier (in this case, standard2) that exceeds the allowed quota. The error suggests that we sre using 0 out of 0 quota, meaning you have no available quota for this tier. The recommended fix is to submit a quota increase request using the guidelines provided in the error message:

```
ServiceQuotaExceeded: Operation would exceed 'standard2' tier service quota. You are using  
0 out of 0 'standard2' tier service quota. If you need more quota, please submit a quota  
increase request following: https://aka.ms/AddQuotaSubscription.
```

> [!TIP]
> Please follow this link to review the process for [Request a quota increase](https://learn.microsoft.com/en-us/azure/quotas/quickstart-increase-quota-portal#request-a-quota-increase)

### Workaround 

> In the meantime, you can decrease the search service SKU to standard basic since you don't have enough quota. Once the quota is accepted, you can redeploy the service with the right quota assigned.

1. After initializing the project using the azd templates, navigate to the `infra` folder, where you'll find a file named `main.bicep`. For example: [GPT-RAG_SolutionAccelerator/infra/main.bicep](./GPT-RAG_SolutionAccelerator/infra/main.bicep)
2. In the `AI search SKU name` configuration section, you can modify the SKU being used. To do this, for example update the definition in line [336, which currently references standard2/standard](https://github.com/MicrosoftCloudEssentials-LearningHub/RAG-ChatBot-Implementation/blob/main/GPT-RAG_SolutionAccelerator/infra/main.bicep#L386), and replace it with the definition in line [335, which specifies standard/basic](https://github.com/MicrosoftCloudEssentials-LearningHub/RAG-ChatBot-Implementation/blob/main/GPT-RAG_SolutionAccelerator/infra/main.bicep#L385)

    <https://github.com/user-attachments/assets/8cc518e2-12f7-427e-9572-ecdccb931a86>

<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1309-limegreen" alt="Total views">
  <p>Refresh Date: 2026-07-01</p>
</div>
<!-- END BADGE -->
