# Initial AI Questions - Overview 

Costa Rica

[![GitHub](https://img.shields.io/badge/--181717?logo=github&logoColor=ffffff)](https://github.com/)
[Cloud2BR OSS - Learning Hub](https://github.com/Cloud2BR-MSFTLearningHub)

Last updated: 2026-04-06

----------

| **Category**              | **Question to Ask**                                                                 | **Example Response**                                                                 | **Purpose** |
|--------------------------|-------------------------------------------------------|------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| **Business Objective**   | What problem are you trying to solve with AI?                                       | `We want to reduce manual ticket triage time.`                                     | Understand the core use case and business value.|
| **AI Use Case Type**     | Is this a predictive, generative, or classification use case?                       | `We want to predict equipment failure before it happens.`                          | Helps determine the AI model type and architecture.|
| **Data Availability**    | What kind of data do you have access to?                                            | `We have historical logs, sensor data, and incident reports.`                      | Assesses data readiness and integration needs.|
| **Data Location**        | Where is your data stored (cloud, on-prem, hybrid)?                                 | `Most of our data is in Azure Data Lake.`                                          | Determines data pipeline and access strategy.|
| **Real-Time vs Batch**   | Do you need real-time insights or is batch processing sufficient?                   | `Real-time alerts are critical for us.`                                            | Influences infrastructure and model deployment strategy.|
| **Integration Points**   | What systems will this AI solution need to integrate with?                          | `ServiceNow, Jira, and our internal monitoring tools.`                             | Identifies APIs, connectors, and integration complexity.|
| **User Interaction**     | Will end users interact with the AI directly (e.g., chatbot) or indirectly?         | `It will be embedded in our internal dashboard.`                                  | Helps define UI/UX and delivery method.|
| **Security & Compliance**| Are there any compliance or data privacy requirements (e.g., HIPAA, GDPR)?         | `Yes, we must comply with SOC 2 and GDPR.`                                         | Determines constraints on data handling and model training.|
| **Preferred Cloud**      | Do you have a preferred cloud provider or existing cloud contracts?                 | `We’re primarily an Azure shop.`                                                   | Guides service selection (e.g., Azure ML, AWS SageMaker, GCP Vertex AI).|
| **AI Maturity**          | Have you used AI/ML in production before?                                           | `We’ve done some POCs but nothing in production.`                                  | Assesses readiness and need for foundational support.|
| **Model Ownership**      | Do you plan to build your own models or use prebuilt ones (e.g., OpenAI, Azure AI)? | `We’d prefer to fine-tune a prebuilt model.`                                       | Helps scope the project and choose between custom vs. managed services.|
| **Monitoring Needs**     | How will you monitor and evaluate model performance?                                | `We’ll need dashboards and alerts for drift and accuracy.`                         | Ensures observability and governance are planned.|
| **Scalability**          | How many users or transactions do you expect the AI to handle?                      | `We expect 10,000+ daily interactions.`                                            | Determines infrastructure sizing and cost implications.|
| **Budget & Timeline**    | What’s your budget and timeline for this initiative?                                | `We have a 3-month window and a $50K budget.`                                      | Helps prioritize scope and feasibility.|
| **Success Metrics**      | How will you measure the success of this AI solution?                               | `Reduction in ticket resolution time by 30%.`                                      | Aligns technical goals with business KPIs.|

<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1309-limegreen" alt="Total views">
  <p>Refresh Date: 2026-07-01</p>
</div>
<!-- END BADGE -->
