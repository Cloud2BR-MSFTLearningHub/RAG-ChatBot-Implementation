# Application Redeployment - Quick Guide

Costa Rica

[![GitHub](https://img.shields.io/badge/--181717?logo=github&logoColor=ffffff)](https://github.com/)
[Cloud2BR OSS - Learning Hub](https://github.com/Cloud2BR-MSFTLearningHub)

Last updated: 2026-04-06

------------------------------------------

> How to redeploy your application using the Azure Developer CLI:

1. Use the Virtual Machine connected via Bastion, log into the VM using the username and authenticate with the password stored in the keyvault.
2. Go to the environment where you developed your application and navigate to the deploy folder. For example, it would be the folder created during [this step](https://github.com/MicrosoftCloudEssentials-LearningHub/RAG-ChatBot-Implementation/tree/main?tab=readme-ov-file#step-8-application-deployment)
3. Logs you into Azure Developer CLI, run: `azd auth login.`
4. Logs you into your Azure account, run: `az login`
5. Updates your environment settings with the latest configuration, run: `azd env refresh`
6. Builds and packages your application code into deployable artifacts without deploying them to Azure, run: `azd package`
7. Deploys your project to Azure, run: `azd deploy`

<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1309-limegreen" alt="Total views">
  <p>Refresh Date: 2026-07-01</p>
</div>
<!-- END BADGE -->
