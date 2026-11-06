# Agentic Content Platform: Program Setup Portfolio

> **Portfolio sample, fictional scenario.** "Aurelis Pharma" and every person, team, date and number here are invented to show how I set up and run a technical program. Nothing here comes from any employer's or client's confidential data. The product names (Adobe Workfront, AEM Assets, Adobe Journey Optimizer, Veeva PromoMats) are real systems I reference as integration points. No vendor endorsement is implied.

## The scenario

Aurelis Pharma's US Commercial Marketing team spends **weeks** taking a promotional asset from brief to approved: copywriting, agency rounds, and Medical/Legal/Regulatory (MLR) review in Veeva PromoMats. Leadership has funded an **Agentic AI Platform**. Its anchor module is **Content Composer**, an AI agent that drafts on-brand, claims-compliant first drafts from an approved claims library and routes them to human review.

I join as **Hybrid TPM / Business Analyst** on day 1. There's no Jira project, no RAID log, no status cadence, and three teams in two time zones:

| Team | Role in program | Location |
|---|---|---|
| US Commercial Marketing (Business) | Product owner, brand content, user acceptance | US Pacific |
| DSML: Data Science & ML | Agent design, prompts, retrieval (RAG), evaluation | US + Global |
| DT: Digital Technology | Platform engineering, Adobe/Veeva integrations, security | Global (CET) |
| Global Marketing Excellence | Global brand standards, reuse of modules in other markets | Global (CET) |

This repo is what I'd produce in the **first 3–4 weeks**.

## What's inside

| # | Artifact | What it shows |
|---|---|---|
| 01 | [Program charter](01-program-setup/program-charter.md) | Scope, objectives with target ranges, RACI, governance cadence, AI governance & regulatory alignment (NIST AI RMF, Part 11) |
| 01 | [Jira & Confluence structure](01-program-setup/jira-confluence-structure.md) | Issue hierarchy, dependency-tracking options, workflow, Definition of Ready/Done with AI evaluation gates, space tree, cross-time-zone ceremonies |
| 02 | [RAID log](02-tracking/raid-log.csv) | 21 scored (impact × likelihood) Risks, Assumptions, Issues and Dependencies with owners, review dates and mitigations |
| 02 | [Weekly status report](02-tracking/status-report.md) | Reusable template + a filled-in example week (RAG, milestones, decisions needed) |
| 03 | [Dependency map & roadmap](03-dependencies/dependency-map.md) | Cross-team dependency graph, dependency register, milestone Gantt |
| 04 | [Epic → user stories](04-requirements/epic-to-stories.md) | One epic broken into 11 stories: Given/When/Then criteria for fixed rules, evaluation thresholds for AI quality, plus a release gate for model and prompt changes |
| 04 | [Jira import file](04-requirements/jira-import.csv) | The same stories as a CSV ready for Jira import |
| 05 | [As-is / to-be workflow](05-process/as-is-to-be.md) | Current vs. future content workflow with human-in-the-loop (HITL) review points |
| 06 | [Agent functional spec](06-agent-spec/agent-functional-spec.md) | Bounded agent design: inputs/outputs, retrieval (RAG) rules, prompt design with claim slots, tool permissions (MCP-ready), layered guardrails, failure modes, evaluation, build/buy/combine vs. Veeva AI and Adobe GenStudio, OWASP 2026 security mapping, cost and resilience |
| 07 | [Integration map](07-integrations/integration-map.md) | Adobe Workfront, AEM Assets and Journey Optimizer + Veeva Vault PromoMats (incl. Veeva AI Quick Check): landscape, end-to-end sequence, system-to-requirement matrix, data and status mappings, spikes |
| 08 | [Platform assessment](08-assessment/vendor-assessment.md) | Build, buy or combine across Adobe GenStudio, Adobe CX Enterprise Coworker, Veeva AI for PromoMats and specialist vendors: knock-outs (incl. model-change transparency), weighted rubric with scoring anchors, usage-based TCO, portability, evidence plan, worked example with sensitivity check, AI-specific contract terms |
| 09 | [Business Requirements Document](09-brd/business-requirements.md) | Business problem, objectives, users, 14 business requirements (incl. business readiness and AI-assisted disclosure), compliance business rules, and a traceability matrix that surfaces 3 gaps |

All diagrams are [Mermaid](https://mermaid.js.org/) and render directly on GitHub.

## How I approached it

1. **Make the work visible before optimizing it.** Charter, Jira structure and RAID log come first, so every team sees one picture of scope, owners and risks.
2. **Track dependencies as first-class work.** Three teams own pieces of one user journey. Every cross-team handoff gets an owner, a date and a Jira link (see `03-dependencies`).
3. **Write stories a developer and a tester can both act on.** Fixed rules get Given/When/Then criteria. AI quality varies from run to run, so it gets **thresholds measured on an evaluation set and a red-team set**. Hard compliance rules stay at zero tolerance.
4. **Design human review in, not on.** In regulated content, AI output is a *draft* until a human approves it. The to-be workflow makes each HITL checkpoint explicit, and the agent has no write access to any system of record.
5. **Treat AI changes like releases.** The model version is pinned, prompts are versioned, and every change passes an evaluation gate. Governance maps to NIST AI RMF and security maps to the OWASP 2026 lists, rather than being invented from scratch.
6. **Don't rebuild what the stack already does.** Where Veeva or Adobe ship native AI (pre-MLR checks, brand intelligence, brief agents), the spec makes an explicit build, buy or combine call, backed by a test.
7. **Respect the time-zone gap.** Ceremonies sit in the shared US–CET overlap window. Everything else is async in Confluence.

## Roadmap for this repo

- [x] Tier 1: program setup, tracking, dependencies, stories, workflow
- [x] Tier 2: agentic AI functional spec (prompts, retrieval, tools, guardrails); Adobe + Veeva integration map
- [x] Tier 3: next-gen content-AI vendor assessment with scoring rubric; Business Requirements Document (BRD)

## About me

**Kenneth Hwang**, Program Manager with 7+ years across AI/ML platform delivery, platform governance and Trust & Safety. I've set up Jira/Confluence structures for AI/ML module rollouts, written user stories and acceptance criteria for AI workflow features, and aligned delivery across North American, European and Asian teams. Bilingual English/Mandarin.

📧 mykenneth64@gmail.com · 📍 San Mateo, CA
