# Microsoft Copilot Product & Platform Decision Guide - Overview

> How to choose between `Microsoft 365 Copilot`, `Copilot Studio`, and `Azure AI Foundry (Azure AI Studio)` for your scenario.

Costa Rica

[![GitHub](https://img.shields.io/badge/--181717?logo=github&logoColor=ffffff)](https://github.com/)
[Cloud2BR OSS - Learning Hub](https://github.com/Cloud2BR-MSFTLearningHub)

Last updated: 2026-07-01

----------

<details>
<summary><b>List of References</b> (Click to expand)</summary>

- [Microsoft Copilot Studio pricing](https://azure.microsoft.com/en-us/pricing/details/copilot-studio/?msockid=38ec3806873362243e122ce086486339)
- [Get access to Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/billing-licensing#get-access-to-copilot-studio) - pricing overview 
- [AI strategy & decision tree](https://learn.microsoft.com/azure/cloud-adoption-framework/scenarios/ai/strategy) - Cloud Adoption Framework
- [Which Copilot is right for your org](https://learn.microsoft.com/copilot/microsoft-365/which-copilot-for-your-organization) - Microsoft 365 Copilot
- [Choose the right agent solution](https://learn.microsoft.com/microsoft-365/agents-sdk/choose-agent-solution) - Copilot Studio vs SDKs vs Azure AI
- [Copilot Studio overview](https://learn.microsoft.com/microsoft-copilot-studio/fundamentals-what-is-copilot-studio) - Copilot Studio
- [Declarative agents tool comparison](https://learn.microsoft.com/microsoft-365-copilot/extensibility/declarative-agent-tool-comparison) - Declarative Agents
- [Extensibility planning guide (agents for M365 Copilot)](https://learn.microsoft.com/microsoft-365-copilot/extensibility/planning-guide) - Extensibility Planning
- [Training path: Build a foundation to build AI agents & extend M365 Copilot](https://learn.microsoft.com/training/paths/build-foundation-extend-microsoft-365-copilot/) - Training Path

</details>

<details>
<summary><b>Table of Content</b> (Click to expand)</summary>

- [Where to start?](#where-to-start)
- [Quick decision tree](#quick-decision-tree)
- [Copilot Studio vs Azure AI Foundry Azure AI Studio](#copilot-studio-vs-azure-ai-foundry-azure-ai-studio)
- [Implementation considerations security, data, networking](#implementation-considerations-security-data-networking)
- [FAQ](#faq)
  - [Q1. Is Copilot Studio only for chat?](#q1-is-copilot-studio-only-for-chat)
  - [Q2. When do I prefer Azure AI Foundry?](#q2-when-do-i-prefer-azure-ai-foundry)
  - [Q3. Can I extend Microsoft 365 Copilot with my own domain agent?](#q3-can-i-extend-microsoft-365-copilot-with-my-own-domain-agent)

</details>

> [!IMPORTANT]
> This is a practical `selection guide` synthesized from Microsoft Learn. For official canonical guidance (which evolves), always verify the linked docs: [AI Strategy decision tree](https://learn.microsoft.com/azure/cloud-adoption-framework/scenarios/ai/strategy) and [Which Copilot is right for you](https://learn.microsoft.com/copilot/microsoft-365/which-copilot-for-your-organization)

## Where to start?

1. **Clarify the goal**: productivity in M365 apps, a custom line-of-business agent, or a full-blown AI app/platform?
2. **Match to service model**: **SaaS (Copilots)** for speed, **PaaS (Azure AI)** for control, **IaaS** for maximum customization. Read more about it here [Implementation considerations security, data, networking](#implementation-considerations-security-data-networking)

## Quick decision tree 

> [!TIP]
>
> - If you need: → choose `Microsoft 365 Copilot`.
>   - `in‑app AI in Word/Excel/PowerPoint/Teams with enterprise protections` 
> - If you need: → choose `Copilot Studio`.
>   - a `custom business agent` (low-code)
>   - `multi‑channel` (Teams/web)
>   - automation with `Power Platform`
>   - quick time‑to‑value 
>- If you need:  → choose `Azure AI Foundry (Azure AI Studio)/ Azure Open AI`.
>   - a `developer platform` for `RAG`
>   - multi‑agent patterns
>   - `model choice`
>   - evaluations
>   - deep integration
>- If you simply want: → `Microsoft Copilot (consumer)`
>   - a `web-grounded personal assistant` (not for sensitive work data)
>- If you need **AI assistance for coding/development**: → choose `GitHub Copilot`
>   - AI-powered code completions, chat, and PR reviews in your IDE
>   - Works in VS Code, JetBrains, Vim, and more
>   - Supports 30+ programming languages
>   - Requires a [GitHub Copilot subscription](https://github.com/features/copilot)

<img width="846" height="1048" alt="ai-chat-decision-flow drawio" src="docs/ai-chat-decision-flow.png" />

> [!TIP]
> <img src="https://img.shields.io/badge/GitHub_Copilot-AI_Coding_Assistant-6e40c9?style=flat&logo=githubcopilot&logoColor=white" alt="GitHub Copilot" height="22"/> &nbsp; **Need AI assistance for your code?** → Use **[GitHub Copilot](https://github.com/features/copilot)**!
>
> GitHub Copilot is your AI-powered coding assistant, available directly in your IDE. It provides intelligent code completions, an in-editor chat, pull request summaries, and automated code reviews. If your goal is to **write, understand, or review code faster**, GitHub Copilot is the right choice.
>
> | Feature | Details |
> |---------|---------|
> | **Where it works** | VS Code, JetBrains, Vim/Neovim, Visual Studio, Azure Data Studio, Xcode |
> | **What it does** | Code completions, inline chat; slash commands: `/explain` (understand code), `/fix` (fix issues), `/test` (generate tests), PR summaries |
> | **Languages** | 30+ including Python, JavaScript, TypeScript, Go, Java, C#, C++ |
> | **Plans** | [Individual, Business, Enterprise](https://github.com/features/copilot#pricing), **free tier** (2,000 completions + 50 chats/month) available to all GitHub users |
> | **Docs** | [GitHub Copilot Documentation](https://docs.github.com/copilot) |

> [!NOTE]
> `When users don't want/need to create their own interface or customized view`, they can `leverage the AI integrated into our products and services, depending on their needs.` For example, if they require visualizations capabilities with AI assistance, they can use the AI already built into `Fabric/Power Bi to generate reports, ask questions, etc.` Click here to read more about it [AI Strategy decision tree](https://learn.microsoft.com/azure/cloud-adoption-framework/scenarios/ai/strategy) 

Click here to [access the diagram](./docs/ai-chat-decision-flow.drawio)

<details>
<summary><b>More details</b> (Click to expand)</summary>

| Scenario                                                                                                  | Choose                                                  | Why this fits                                                                    | Key notes                                                                                                                                                                                                                                          |
| --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------- | -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Employees want AI in **Word/Excel/PowerPoint/Outlook/Teams** with enterprise-grade protections            | **Microsoft 365 Copilot**                               | Natively integrated experiences; work & web chat; governed by M365 controls      | Requires org licensing; respects Microsoft Graph permissions.                                                                           |
| Build a **custom agent** quickly, connect business data, **automate** flows, publish to **Teams or web**  | **Copilot Studio**                                      | Low-code authoring, topics, knowledge sources, **agent flows**, Power Automate   | Great for fusion teams; supports channels via Azure Bot Service.|
| Develop a **RAG** app or **multi-agent** solution with fine control over models, evals, safety, and infra | **Azure AI Foundry (Azure AI Studio)**                  | Unified SDK/APIs, integrates Azure OpenAI & Cognitive Services, deep ops control | Best for pro-code; aligns with PaaS patterns in CAF.                  |
| Extend M365 Copilot with **task-specific agents** using declarative tools                                 | **Agents for M365 Copilot** (via Copilot Studio & SDKs) | Purpose-built extensions that run inside M365 Copilot orchestrator               | See tool comparison & planning guide.   |
| Personal, **non-sensitive** queries with image creation                                                   | **Microsoft Copilot (consumer)**                        | Free web-grounded assistant                                                      | Don’t use for confidential work content. |
| Need **AI assistance for coding** — completions, chat, PR reviews, test generation — in your IDE         | <img src="https://img.shields.io/badge/GitHub-Copilot-6e40c9?logo=githubcopilot&logoColor=white" alt="GitHub Copilot" height="18"/> **[GitHub Copilot](https://github.com/features/copilot)** | AI pair programmer embedded in your editor; works across 30+ languages | **Free tier** available (2,000 completions + 50 chat messages/month); paid Individual, Business & Enterprise plans also available. |

</details>

## Copilot Studio vs Azure AI Foundry (Azure AI Studio)

| Dimension             | **Copilot Studio**                                                                         | **Azure AI Foundry (Azure AI Studio)**                                              |
| --------------------- | ------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------- |
| **Audience**          | Fusion teams, citizen developers                                                           | Pro-code developers                                                                 |
| **Approach**          | **Low-code SaaS** agent builder with topics, knowledge, **agent flows**, plugins           | **PaaS** development platform with unified SDKs/APIs, RAG, multi-agent, evals       |
| **Typical use**       | Helpdesk bots, HR/IT FAQ, approvals, guided flows, Teams agents                            | Custom RAG apps, multi-agent orchestration, domain copilots with bespoke logic      |
| **Data & connectors** | Prebuilt/custom plugins, Power Platform connectors; Azure AI Search supported as knowledge | Bring your own data stores; Azure AI Search, vector DBs; full orchestration control |
| **Channels**          | Publish to **Teams**, web, channels via Azure Bot Service                                  | You host and expose services; integrate into custom apps, Teams, M365 via SDKs      |
| **Governance**        | Power Platform governance, DLP, environment controls                                       | Azure governance (RBAC, VNets, Private Link), CI/CD, responsible AI reviews         |
| **When to pick**      | Rapid time-to-value; low-code; align with Power Platform ops                               | Need model choice, fine-grained data/infra control, complex pipelines & testing     |

## Implementation considerations (security, data, networking)

> [!TIP]
>
> - ![fastest](https://img.shields.io/badge/fastest-brightgreen?style=flat) Need fastest productivity impact across M365? `Choose SaaS (M365 Copilot/Copilot Studio).`
> - ![control](https://img.shields.io/badge/customization-orange?style=flat) Building a domain copilot or RAG API with enterprise controls? `Choose PaaS (Azure AI Foundry).`
> - ![flex](https://img.shields.io/badge/flexibility-blue?style=flat) Must run in tightly isolated environments or custom GPU stacks? `Choose IaaS.`
> - ![control](https://img.shields.io/badge/customization-orange?style=flat) Unsure? Start on `PaaS for speed + control; move edge cases to IaaS if required.`

<details>
<summary><b>More details</b> (Click to expand)</summary>

| Dimension | ![SaaS](https://img.shields.io/badge/SaaS-fastest-brightgreen?style=flat) Microsoft Copilots | ![PaaS](https://img.shields.io/badge/PaaS-control-orange?style=flat) Azure AI Foundry | ![IaaS](https://img.shields.io/badge/IaaS-flexibility-blue?style=flat) Self-managed on VMs/Kubernetes |
|---|---|---|---|
| Service model fit | Fastest path to value for productivity and common copilots | High control and customization for app/platform copilots | Maximum flexibility for bespoke/regulated builds |
| Primary use cases | M365 Copilot, Copilot Studio solutions, plugin/Graph-powered automations | RAG apps, domain copilots, tool-use/orchestration, API integrations | Custom model hosting, air‑gapped or non-PaaS constraints, specialized GPUs |
| Speed to value | Minutes to days | Days to weeks | Weeks to months |
| Customization depth | Low–medium (prompts, plugins, Graph connectors) | High (Prompt Flow, tools/functions, agents, vector/RAG, custom APIs) | Full stack (models, infra, networking, storage, schedulers) |
| Model choice | Microsoft-hosted models inside M365 | Azure OpenAI, Azure AI model catalog (OSS/commercial), bring-your-own endpoints | Any model you deploy/manage (open‑source or licensed) |
| Data readiness & access | Govern via Microsoft Graph permissions, sensitivity labels, Purview; minimize oversharing | Plan grounding stores (Azure AI Search, Cosmos DB, Storage); index and chunking strategy | You design data paths, stores, and indexing end‑to‑end |
| Networking & isolation | Tenant/Service boundary managed by Microsoft | Private Link, VNet integration, Managed VNets, regional isolation | Full VNet/subnet control, firewalls, proxies, private DNS |
| Egress control | Built-in guardrails, limited customization | Private endpoints, NSGs, UDRs, forced tunneling; restrict outbound to PaaS | You own all egress/policy controls |
| Safety & content filtering | Built-in safety filters and enterprise policies | Azure AI Content Safety, safety system prompts, abuse monitoring options | DIY or integrate third‑party safety stack |
| Compliance & data residency | Inherits Microsoft enterprise compliance in M365 | Choose Azure regions; align with org policies and regulators | Fully your responsibility to implement and evidence |
| Identity & access | Entra ID + Microsoft Graph; Power Platform DLP | Entra ID (RBAC), Managed Identity, Key Vault, Azure Policy | Your IAM, secrets, RBAC, and policy framework |
| Cost model | Per user/feature licensing | Consumption-based (tokens, search, storage, inference) | Infra + software + ops (VMs/GPU/K8s + licenses) |
| Scaling & ops | Microsoft manages | Azure platform-managed with quotas and SLAs | You provision, scale, patch, monitor |
| Governance & lifecycle | Power Platform environments, DLP policies, solution packaging | Azure Policy/Blueprints, DevOps pipelines, IaC (Bicep/Terraform) | Your SDLC, IaC, change control, audits |
| Risks / trade‑offs | Less deep customization; feature roadmap dependency | Service quotas/limits; more components to secure | Highest ops burden; capacity planning and reliability on you |

</details>

<img width="858" height="1546" alt="image" src="https://github.com/user-attachments/assets/702b07f1-4a92-4e76-82ef-601aec91c9ea" />

From [AI Strategy decision tree](https://learn.microsoft.com/azure/cloud-adoption-framework/scenarios/ai/strategy) 

> To understand more about [Introduction to Microsoft Azure: Describe cloud concepts](https://learn.microsoft.com/en-us/training/paths/microsoft-azure-fundamentals-describe-cloud-concepts/) click here, also find a quick summary:

<img width="709" alt="image" src="https://github.com/brown9804/DevOps-Agile-Cloud_path/assets/24630902/7bc73a87-3b57-4f41-87de-5e72f3dfc6c7">

From [Cloud computing - Service Models: SAAS, PAAS, IAAS - Which Is Better For Business](https://dev.to/artemkobilinskiy/cloud-service-models-saas-paas-iaas-which-is-better-for-business-574k), more details [here about it](https://qualitapps.com/en/what-are-the-iaas-paas-and-saas-cloud-service-models/)

## FAQ

### Q1. Is Copilot Studio only for chat?

> It builds `agents` (beyond simple chat) that can call flows, connect to data, and act across channels (Teams/web). Please read more about it here [Copilot Studio overview](https://learn.microsoft.com/microsoft-copilot-studio/fundamentals-what-is-copilot-studio) 

### Q2. When do I prefer Azure AI Foundry?

> When you need `RAG/multi-agent`, model choice, evaluations, and deep integration/testing under your DevOps and networking controls.

### Q3. Can I extend Microsoft 365 Copilot with my own domain agent?

> Yes, use `agents` (declarative) and related SDKs; see the tool comparison and planning guidance. Please read more about here [Declarative agents tool comparison](https://learn.microsoft.com/microsoft-365-copilot/extensibility/declarative-agent-tool-comparison), [Extensibility planning guide (agents for M365 Copilot)](https://learn.microsoft.com/microsoft-365-copilot/extensibility/planning-guide).

<!-- START BADGE -->
<div align="center">
  <img src="https://img.shields.io/badge/Total%20views-1309-limegreen" alt="Total views">
  <p>Refresh Date: 2026-07-01</p>
</div>
<!-- END BADGE -->
