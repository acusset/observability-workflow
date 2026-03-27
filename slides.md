---
theme: default
background: '#0f0f1a'
class: text-center
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
title: AI as an Engineering Teammate
---

# AI as an Engineering Teammate

**Two real workflows already running in production**

---
layout: default
background: '#0f0f1a'
---

# Engineering is increasingly reactive

<br/>

> Every sprint, unplanned work creeps in.  
> Vulnerabilities get flagged, bugs get reported, logs need reading.  
> This work is important — but invisible. It doesn't ship features.

<br/>

```
Sprint capacity ████████████████████░░░░░░░░░░  Planned work
                ████████████████░░░░░░░░░░░░░░  → Reactive work eating in
```

---
layout: three-cols
---

# The Cost Nobody Talks About

::left::

### 🔁 Context switches
Engineers average **2+ unplanned interruptions** per day from security alerts and bug reports

::center::

### 🐛 Vague bug reports
A report with no reproduction steps takes **3× longer** to investigate than a detailed one

::right::

### 🔐 CVEs sit unactioned
Vulnerability alerts often go unresolved for **days** — not from negligence, but from unclear ownership

---
layout: center
background: '#0f0f1a'
---

<div style="text-align: center; max-width: 700px; margin: auto;">

# What if AI could own this reactive layer?

<br/>

| 🏗️ Engineer's focus | 🤖 AI's focus |
|---|---|
| Architecture & design | Security triage |
| Shipping features | Bug investigation |
| Customer decisions | Log analysis |
| Code review | Vulnerability reports |

</div>

---
layout: center
background: '#1a1a0f'
---

<div style="font-size: 6rem; opacity: 0.15; font-weight: 900;">01</div>

# Case 1: Vulnerability Management

<div style="opacity: 0.6; margin-top: 1rem;">🔐 When a package has a CVE — the agent takes it from there</div>

---

# A CVE alert lands. Now what?

The manual process every engineer dreads:

```
CVE alert received
      ↓  ⏱
Identify affected packages
      ↓  ⏱
Assess severity across dependency tree
      ↓  ⏱
Plan upgrade path (without breaking changes)
      ↓  ⏱
Test & verify
      ↓  ⏱
Write up findings
```

> Each step requires context, research, and focus.  
> And it usually falls on whoever is unlucky enough to pick it up.

---
layout: two-cols
---

# The agent takes it from here

::left::

**What the agent does:**

1. Calls the **Snyk REST API** to retrieve vulnerability data
2. Scores findings by **CVSS severity**
3. Maps affected packages across the dependency tree
4. Proposes a **safe upgrade path**
5. Flags potential breaking changes

The engineer **reviews and approves** — they don't investigate from scratch.

::right::

**Sample output:**

```json
{
  "scan_date": "2026-03-27",
  "critical": [
    {
      "package": "lodash",
      "current": "4.17.15",
      "cve": "CVE-2021-23337",
      "severity": "CRITICAL",
      "fix": "4.17.21",
      "breaking_changes": false
    }
  ],
  "high": [...],
  "recommended_action": "Safe to upgrade all critical items"
}
```

---
layout: center
---

# From hours to minutes. Consistently.

<br/>

| | Before | After |
|---|---|---|
| ⏱ Triage time | ~3 hours | ~15 minutes |
| 📋 Output quality | Varies by engineer | Standardized |
| 🔁 Context switching | High | Near zero |

<br/>

> *"The agent doesn't get tired. It doesn't skip steps.  
> It doesn't deprioritize a CVE because the sprint is busy."*

---
layout: center
background: '#0f1a1a'
---

<div style="font-size: 6rem; opacity: 0.15; font-weight: 900;">02</div>

# Case 2: Observability & Bug Investigation

<div style="opacity: 0.6; margin-top: 1rem;">🔭 When a user says "something's not working" — AI finds out what</div>

---

# A user says: "something's not working"

The worst kind of bug report:

```
┌─────────────────────────────────────────┐
│  🐛 Bug Report                          │
│─────────────────────────────────────────│
│  Title: Something's not working         │
│  Steps to reproduce: (empty)            │
│  Expected behaviour: (empty)            │
│  Actual behaviour: it just doesn't work │
│  Attachments: none                      │
└─────────────────────────────────────────┘
```

Then the manual investigation begins:

```
Open Datadog  →  ⏱  Find the right timeframe  →  ⏱  
Correlate logs with traces  →  ⏱  Form a hypothesis  →  ⏱  
Write it all up  →  ⏱  (2–3 hours later...)
```

---
layout: three-cols
---

# Give the AI the logs. Get back a bug report.

::left::

**Input: Datadog context**

```
[10:42:03] ERROR POST /api/orders
  TraceID: 7f3a92b1
  Service: order-service
  Duration: 8423ms
  
[10:42:03] WARN DB pool exhausted
  connections: 20/20
  queue_depth: 47
  
[10:42:04] ERROR Timeout
  downstream: payment-service
  waited: 5000ms
```

::center::

<div style="text-align:center; padding-top: 4rem;">

↓

**AI analyses traces + logs**

↓

</div>

::right::

**Output: Structured bug report**

```markdown
## Bug: Order API Timeout

**When:** 2026-03-27 10:42 UTC  
**Service:** order-service  
**Severity:** High  

**Root cause:** DB connection pool 
exhaustion caused cascading timeout 
to payment-service.

**Impact:** All orders during 
10:41–10:44 UTC (~3 min window)

**Recommended fix:** Increase pool 
size or add circuit breaker on 
payment-service calls.
```

---
layout: center
---

# Richer reports. Faster than any human could write.

<br/>

| | Typical manual report | AI-generated report |
|---|---|---|
| Time to produce | 2–3 hours | ~5 minutes |
| Root cause identified | Sometimes | Consistently |
| Affected time window | Rarely specified | Always included |
| Recommended fix | Rarely included | Always included |
| Junior engineer output | Sparse | Senior-level detail |

<br/>

> *"Junior engineers can now produce senior-level investigation output  
> on their very first on-call shift."*

---
layout: two-cols
---

# AI removes the worst parts of the job

::left::

### 🤖 AI handles
- Repetitive investigation
- Blank-page problem
- Cross-referencing data sources
- Structured report writing
- CVE triage and scoring
- Context-switching tax

::right::

### 👷 You handle
- Architectural decisions
- Reviewing & approving AI output
- Customer empathy
- Engineering judgment
- Tradeoffs and priorities
- What to build next

<br/>

> *AI doesn't replace the engineer.  
> It removes the parts engineers  
> shouldn't need to do manually.*

---
layout: center
background: '#0f0f1a'
---

# What else could AI own?

<br/>

<div style="display: flex; flex-wrap: wrap; gap: 1rem; justify-content: center; max-width: 600px; margin: auto;">

```
┌────────────────────┐  ┌────────────────────┐
│ 📝 Incident        │  │ 🔍 PR summaries     │
│    postmortems     │  │    & review prep   │
└────────────────────┘  └────────────────────┘

┌────────────────────┐  ┌────────────────────┐
│ 📦 Release notes   │  │ 🚨 On-call triage   │
│    generation      │  │    & escalation    │
└────────────────────┘  └────────────────────┘

┌────────────────────┐  ┌────────────────────┐
│ 🧪 Test coverage   │  │ 📊 Dependency      │
│    gap analysis    │  │    health reports  │
└────────────────────┘  └────────────────────┘
```

</div>

> *The pattern is always the same: give AI the context,  
> get structured output, engineer validates.*

---
layout: center
background: '#0f0f1a'
---

# AI can handle real engineering work.

## We've proved it.

<br/>

These aren't prototypes or demos.  
They're **running in production today.**

<br/>

> *The question isn't whether AI is ready.  
> It's what we point it at next.*
