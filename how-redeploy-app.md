# Application Redeployment - Quick Guide

> How to redeploy your application using the Azure Developer CLI:

1. Use the Virtual Machine connected via Bastion, log into the VM using the username and authenticate with the password stored in the keyvault.
2. Go to the environment where you developed your application and navigate to the deploy folder. For example, it would be the folder created during [this step](https://github.com/MicrosoftCloudEssentials-LearningHub/RAG-ChatBot-Implementation/tree/main?tab=readme-ov-file#step-8-application-deployment)
3. Logs you into Azure Developer CLI, run: `azd auth login.`
4. Logs you into your Azure account, run: `az login`
5. Updates your environment settings with the latest configuration, run: `azd env refresh`
6. Builds and packages your application code into deployable artifacts without deploying them to Azure, run: `azd package`
7. Deploys your project to Azure, run: `azd deploy`
