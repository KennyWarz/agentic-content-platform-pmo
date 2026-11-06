# Program Charter: Agentic AI Platform, Release 1 (Content Composer)

| Field | Value |
|---|---|
| Program | Agentic AI Platform |
| Anchor module | Content Composer (Release 1) |
| Executive sponsor | VP, US Commercial Marketing |
| Product owner | Director, Marketing Content Operations |
| TPM / BA | Kenneth Hwang |
| Charter version | v0.3, for sign-off at Steering Committee #1 |

## 1. Problem

Getting one HCP-facing promotional email from brief to MLR-approved takes several weeks. Most of that time goes to drafting rounds and MLR rework. A big share of MLR rejections trace back to **claims that aren't in the approved claims library** or **missing references**. Both are problems a well-scoped AI drafting agent can reduce, as long as humans stay accountable for approval.

## 2. Objectives (Release 1)

Targets are **hypotheses to confirm once the baseline is measured** (I-01 in the RAID log). Steering re-confirms them at the end of Phase 1.

| # | Objective | Success measure | Pilot target (hypothesis) |
|---|---|---|---|
| O1 | Cut brief-to-MLR-submission time for in-scope asset types | Median days from brief "Ready" to MLR submission | **30–50% reduction** vs. baseline |
| O2 | Raise first-pass MLR approval rate | Share of MLR rejections caused by claims or references | **50% fewer** claim/reference rejections |
| O3 | Keep 100% human approval before anything leaves the building | AI-generated assets published without MLR approval | **0**, a hard gate rather than a target |
| O4 | Keep AI output trustworthy | Groundedness and red-team results on the evaluation set (see CC-02-03, CC-02-05) | **100%** grounded · **0** harmful drafts released |
| O5 | Build reusable platform pieces for the next AI modules | Retrieval, guardrail, evaluation and audit services documented and reused | Reused by Module 2 **without rebuild** |
| O6 | Marketers actually use it | Share of pilot-brand HCP emails started in Composer | **≥ 60%** by end of pilot |

## 3. Scope

**In scope (R1)**
- Asset types: HCP email (Adobe Journey Optimizer) and web banner copy, **one brand, US market, English**
- Content brief intake from Adobe Workfront
- AI draft generation grounded **only** in the approved claims library and brand guidelines
- Image selection from approved assets in AEM Assets (DAM)
- Packaging and submission to Veeva PromoMats for MLR review
- Generation audit log (model, prompt version, sources used)

**Out of scope (R1)**
- Patient-facing content, non-US markets, translation/localization (planned Module 3)
- AI-generated imagery
- Automatic publishing of any kind
- Personalization/experimentation in Adobe Target or Optimizely (R2 candidate)

## 4. Stakeholders & RACI

R = Responsible · A = Accountable · C = Consulted · I = Informed

| Deliverable | Mktg PO | DSML | DT Platform | MLR / Compliance | Global Mktg Exc. | TPM/BA |
|---|---|---|---|---|---|---|
| Program plan, RAID, status | C | C | C | I | I | **A/R** |
| Epics & priorities | **A** | C | C | C | C | R |
| User stories & acceptance criteria | A | C | C | C | I | **R** |
| Agent design, prompts, RAG, evaluation | C | **A/R** | C | C | I | C |
| Workfront / AEM / Veeva integrations | C | C | **A/R** | I | I | C |
| Guardrail rules (claims, off-label language) | C | R | C | **A** | C | C |
| Security & privacy review | I | C | **A/R** | C | I | C |
| UAT & go-live decision | **A** | C | C | R | I | R |
| Global reuse standards | I | C | C | I | **A** | C |

## 5. Governance cadence

| Forum | Frequency | Attendees | Purpose |
|---|---|---|---|
| Steering Committee | Monthly | Sponsor, PO, DSML lead, DT lead, Compliance | Scope, budget, go/no-go, escalations |
| Program sync (cross-team) | Weekly, in US–CET overlap window | Workstream leads, TPM | Dependencies, RAID review, decisions |
| Sprint ceremonies | 2-week sprints | Delivery team | Planning, refinement, review, retro |
| Global alignment sync | Bi-weekly | US PO, Global Marketing Excellence, TPM | Global standards, reuse, roadmap fit |
| Weekly status report | Every Friday | Distributed to all stakeholders | RAG, milestones, risks, asks |

**Escalation path:** workstream lead → weekly program sync → PO → Steering Committee. Any blocker on the critical path older than 5 business days gets escalated automatically.

## 6. Phases & milestones

| Phase | Exit criteria |
|---|---|
| **0. Mobilize** (2 wks) | Charter signed · Jira/Confluence live · RAID baselined · baseline metrics agreed |
| **1. Define** (4 wks) | R1 epics refined · stories Ready for first 2 sprints · guardrail rules approved by Compliance · integration designs signed off |
| **2. Build** (3 sprints) | Integrations working end-to-end in test · agent passes evaluation thresholds |
| **3. Validate** (3 wks) | UAT complete · MLR pilot on 10 real briefs · security sign-off |
| **4. Pilot launch** | Go/no-go at Steering Committee · hypercare plan in place |

## 7. Assumptions & constraints

- An approved, machine-readable claims library exists or can be exported from Veeva (tracked as A-01 in RAID).
- Enterprise LLM access has been cleared by Security for internal, non-patient data.
- MLR reviewers are available for a pilot of about 10 assets during Phase 3.
- The Global DT team works in CET. Live overlap with US Pacific is about 1 hour per day.

## 8. AI governance & regulatory alignment

The program doesn't invent its own AI governance. It plugs into recognized frameworks and the company's existing quality and compliance processes. Compliance and Quality confirm how each item applies before Phase 2.

| Framework / regulation | What it means for this program | Where it's handled |
|---|---|---|
| **NIST AI Risk Management Framework** (Govern · Map · Measure · Manage) | Structure for AI risk work: owners and policy (Govern), documented use case and risks (Map), evaluation metrics (Measure), guardrails, release gate and monitoring (Manage) | RACI · RAID log (R-02, R-08, R-09) · CC-02-05 · CC-02-11 |
| **ISO/IEC 42001** (AI management systems) | If the company is certified or pursuing it, the platform's AI controls are documented to fit its AI management system | Confluence `20 AI / DSML` · to confirm with Quality |
| **FDA 21 CFR Part 11** (electronic records & signatures) | MLR approvals happen inside Veeva PromoMats, the validated system of record. Composer's own audit trail is secure, time-stamped and tamper-proof, so the record of how a draft was made holds up to inspection | CC-02-08 · CC-02-10 |
| **FDA Form 2253** (submitting promotional materials at first use) | Unchanged. Regulatory still owns submission. Composer only makes sure the approved piece carries a complete reference package | Out of scope for R1; confirm hand-off with Regulatory |
| **Privacy (e.g. HIPAA)** | No patient data in briefs, prompts or outputs. Brief form validation rejects it | NFRs in `04-requirements` · A-02 |
| **EU AI Act** | Not in scope for a US-only R1, but must be assessed before any reuse in EU markets (R2 localization) | Global Reuse Register · Steering decision before R2 |

**Model card:** before pilot launch, DSML publishes a one-page model card on Confluence covering intended use, out-of-scope uses, evaluation results, known limits and the pinned model version.
