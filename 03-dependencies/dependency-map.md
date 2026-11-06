# Cross-Team Dependency Map & Roadmap

> IDs match the [RAID log](../02-tracking/raid-log.csv).

## 1. Who needs what from whom

Arrows point from the **delivering** team to the **consuming** team. Red = critical path.

```mermaid
flowchart LR
    subgraph COMP["Compliance / MLR"]
        GR["Guardrail rule set<br/>(D-03)"]
        CL["Claims library attestation<br/>(A-01)"]
    end
    subgraph GLB["Global Marketing Excellence (CET)"]
        BS["Brand voice & template standards<br/>(D-05)"]
    end
    subgraph DSML["DSML"]
        RET["Claims retrieval API<br/>(D-01)"]
        GSV["Guardrail service"]
        AG["Content Composer agent"]
    end
    subgraph DT["Digital Technology (CET)"]
        WF["Workfront brief trigger<br/>(D-04)"]
        DAM["AEM Assets image API"]
        VV["Veeva PromoMats connector<br/>(D-02)"]
    end
    subgraph MKT["US Commercial Marketing"]
        UAT["UAT & MLR pilot"]
    end

    CL --> RET
    GR --> GSV
    BS --> AG
    RET --> AG
    GSV --> AG
    WF --> AG
    DAM --> AG
    AG --> VV
    VV --> UAT
    AG --> UAT

    linkStyle 0,3,7,8 stroke:#d62728,stroke-width:3px
```

**Critical path:** claims retrieval → Composer agent → Veeva connector → UAT/MLR pilot. The Veeva connector (D-02) is the least certain link, because there's no sandbox yet (R-04). That's why it leads the status report.

## 2. Dependency register

| ID | Deliverable | From → To | Needed by | Committed | Status | Fallback if late |
|---|---|---|---|---|---|---|
| D-01 | Claims retrieval API (claim + reference IDs) | DSML → Composer | 2027-02-26 | 2027-02-26 | 🟢 On track | Composer builds against mock endpoint |
| D-02 | Veeva PromoMats submission connector | DT → Composer | 2027-03-12 | TBD | 🔴 At risk | Manual PDF package upload for pilot (adds ~30 min per asset) |
| D-03 | Approved guardrail rule set | Compliance → DSML | 2027-02-12 | 2027-02-11 | 🟢 On track | Verbatim-claims-only mode, which needs fewer rules |
| D-04 | Workfront brief form + webhook | DT → Mktg/Composer | 2027-02-26 | 2027-02-24 | 🟢 On track | Brief entered directly in Composer UI |
| D-05 | Brand standards in usable format | Global → DSML | 2027-02-05 | 2027-02-05 | ✅ Done | n/a |

**How I run it:** each row is a `Dependency` issue in Jira. The consuming team sets *Needed by* and the delivering team sets *Committed*. Any gap between those two dates is discussed in the weekly program sync. A dependency with no committed date after 5 business days goes to the Steering Committee.

## 3. Release 1 roadmap

```mermaid
gantt
    title Agentic AI Platform R1: Content Composer
    dateFormat YYYY-MM-DD
    axisFormat %b %d

    section Program
    Mobilize (charter, Jira, RAID)       :done,    p0, 2027-01-04, 2027-01-15
    M0 Charter signed                    :milestone, done, m0, 2027-01-15, 0d
    Define (epics, stories, designs)     :active,  p1, 2027-01-18, 2027-02-12
    Build (3 sprints)                    :         p2, 2027-02-15, 2027-03-26
    Validate (UAT + MLR pilot)           :         p3, 2027-03-29, 2027-04-16
    M4 Pilot go/no-go                    :milestone, m4, 2027-04-20, 0d

    section Compliance
    Guardrail rule set (D-03)            :active,  c1, 2027-01-18, 2027-02-12
    MLR pilot reviews                    :         c2, 2027-03-29, 2027-04-16

    section DSML
    Claims extraction spike              :done,    d0, 2027-01-18, 2027-01-29
    Retrieval API (D-01)                 :         d1, 2027-02-01, 2027-02-26
    Guardrail service                    :         d2, 2027-02-15, 2027-03-12
    Agent + evaluation                   :         d3, 2027-02-15, 2027-03-26

    section Digital Technology
    Workfront trigger (D-04)             :active,  t1, 2027-01-25, 2027-02-26
    AEM Assets integration               :         t2, 2027-02-15, 2027-03-12
    Veeva connector (D-02, at risk)      :crit,    t3, 2027-02-15, 2027-03-12
    Security review                      :         t4, 2027-03-15, 2027-03-26

    section Marketing
    Co-design sessions                   :done,    k1, 2027-01-25, 2027-02-05
    UAT                                  :         k2, 2027-03-29, 2027-04-09
```
