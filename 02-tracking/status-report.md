# Weekly Status Report

> Part 1 is the reusable template; Part 2 is a filled-in example week.

---

## Part 1: Template

**Program:** {name} · **Week ending:** {date} · **Phase:** {phase} · **Author:** {TPM}

### Overall status: 🟢 / 🟡 / 🔴
{One sentence: are we on track for the next milestone, and if not, why and what's the ask?}

| Workstream | Status | Trend | Summary |
|---|---|---|---|
| {Workstream} | 🟢/🟡/🔴 | ↑ → ↓ | {one line} |

### Milestones
| Milestone | Baseline | Forecast | Status |
|---|---|---|---|

### Done this week
-

### Next week
-

### Top risks & issues (from RAID)
| ID | Item | Severity | Owner | Next step | Due |
|---|---|---|---|---|---|

### Decisions needed
| # | Decision | Needed from | Needed by | Impact if late |
|---|---|---|---|---|

### RAG definitions
- 🟢 **Green:** on track for the next milestone, no help needed
- 🟡 **Amber:** milestone at risk; mitigation in place, may need help
- 🔴 **Red:** milestone will slip without a decision or resource from leadership

### RAID scoring (used in the [RAID log](raid-log.csv))
**Score = Impact × Likelihood**, each rated 1 (low) to 3 (high). For issues, likelihood is 3 (already happening). For dependencies, likelihood means the chance of arriving late.

| Score | Severity | Review rule |
|---|---|---|
| 9 | Critical | Reviewed every week, shown in this report, escalated to Steering if no progress in 5 business days |
| 6 | High | Reviewed every week |
| 3–4 | Medium | Reviewed every 2 weeks |
| 1–2 | Low | Reviewed monthly |

Each entry carries a **Last Reviewed** date. Anything not reviewed on schedule is flagged in the weekly program sync.

---

## Part 2: Example (Week 5)

**Program:** Agentic AI Platform R1 (Content Composer) · **Week ending:** Fri 2027-02-05 · **Phase:** 1. Define (week 3 of 4) · **Author:** Kenneth Hwang, TPM/BA

### Overall status: 🟡 Amber
Define phase is on track, but the **Veeva PromoMats sandbox (R-04 / D-02)** still hasn't been provisioned. That puts the Sprint 2 integration build, and so the Validate start date, at risk. **Ask:** Sponsor to escalate with the Veeva account team by 2027-02-10.

| Workstream | Status | Trend | Summary |
|---|---|---|---|
| Requirements (BA) | 🟢 | ↑ | Epic CC-02 refined: 10 stories Ready, 8 for Sprint 1–2 |
| DSML: agent & retrieval | 🟡 | → | Claims-extraction spike passed on 50/50 claims; retrieval API contract signed off. **Evaluation set 63% labeled**, needed before any AI story can be Done |
| DT: integrations | 🟡 | ↓ | Workfront webhook in dev; **PromoMats sandbox still pending (day 18)** |
| Compliance: guardrails | 🟢 | ↑ | Draft guardrail rule set v0.9 reviewed; final sign-off scheduled 2027-02-11 |
| Global alignment | 🟢 | → | Brand standards delivered (D-05 closed); localization confirmed as R2 |

### Milestones
| Milestone | Baseline | Forecast | Status |
|---|---|---|---|
| M0 Charter signed & tooling live | 2027-01-15 | 2027-01-15 | ✅ Done |
| M1 Stories Ready for Sprints 1–2 | 2027-02-12 | 2027-02-10 | 🟢 |
| M2 Guardrail rules approved | 2027-02-12 | 2027-02-11 | 🟢 |
| M3 End-to-end flow in test | 2027-03-26 | 2027-04-02 | 🟡 depends on D-02 |
| M4 Pilot go/no-go | 2027-04-20 | 2027-04-20 | 🟡 holds if M3 slip ≤ 1 wk |

### Done this week
- Refined Epic CC-02 into 10 stories with Given/When/Then criteria; Compliance reviewed the 3 guardrail stories
- DSML retrieval spike: extracted claim + reference pairs from 50 pilot-brand claims with no manual fixes
- Closed D-05: Global Marketing Excellence published brand-voice standards in a format DSML can use
- Steering #2: confirmed R1 = US/English only; logged EU localization as R2 candidate (closes R-06)

### Next week
- Compliance sign-off on guardrail rule set v1.0 (D-03)
- Sprint 1 planning (2027-02-11)
- Baseline cycle time from 30 sampled assets (I-01)
- Escalate PromoMats sandbox with the Veeva account team

### Top risks & issues
| ID | Item | Severity | Owner | Next step | Due |
|---|---|---|---|---|---|
| R-04 / D-02 | No PromoMats sandbox → submission connector blocked | 🔴 Critical | DT Integration Lead | Sponsor escalation to Veeva; DT builds against API mock meanwhile | 2027-02-10 |
| R-03 | MLR reviewer capacity during pilot | High | PO | 6 of 10 pilot slots booked; ask MLR head for 4 more | 2027-02-19 |
| I-02 | Evaluation dataset not labeled (blocks the AI release gate) | 🔴 Critical | DSML Lead | 38 of 60 historical assets labeled; 40 red-team briefs drafted | 2027-02-12 |
| R-08 | Prompt injection through brief fields | High | DSML Lead | Injection cases added to red-team set; agent tools confirmed read-only | 2027-02-26 |

### Decisions needed
| # | Decision | Needed from | Needed by | Impact if late |
|---|---|---|---|---|
| 1 | Escalate PromoMats sandbox with Veeva | Sponsor | 2027-02-10 | Each week of delay pushes M3 by ~1 week |
| 2 | R1 claims mode: verbatim only vs. light paraphrase | Compliance + PO | 2027-02-11 | Guardrail design and Sprint 1 stories change |
