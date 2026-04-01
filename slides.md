---
theme: default
background: "#0f0f1a"
class: text-center
highlighter: shiki
lineNumbers: false
drawings:
  persist: false
transition: slide-left
title: Security and Observability
layout: cover
---

# Security & Observability

 _Automating as much as possible_

---
layout: fact
---

# I hate context switching

<br/>

<div style="display: flex; justify-content: center; gap: 2rem; align-items: flex-start;">
  <img v-click src="/assets/teams1.jpeg" alt="Teams conversation example 1" style="max-width: 40%; border-radius: 8px; box-shadow: 0 2px 8px #0003;" />
  <img v-click src="/assets/teams2.jpeg" alt="Teams conversation example 2" style="max-width: 40%; border-radius: 8px; box-shadow: 0 2px 8px #0003;" />
</div>

<br/>

<span v-click style="font-size: 1.2rem; color: #e0e0e0;">Interruptions kill your productivity</span>

---
layout: cover
---

# Security

---
layout: three-cols
---

# Open Source Security

::left::

### 🔁 Dependabot

Dependabot opens PRs that only bump dependencies, without checking for breaking changes

::center::

### 🐕 Third Party Tools

Tools like Snyk provide more details about packages and dependencies, and perform regular checks

::right::

### 🔐 CVEs sit unactioned

Vulnerability alerts often go unresolved for **days** unless they are blocking or time is allocated for the team to fix them


---
layout: default
---

# How to deal with vulnerable packages

<ul style="margin-top: 2rem; text-align: left; max-width: 600px; margin-left: auto; margin-right: auto; color: #e0e0e0; font-size: 1.1rem;">
  <li v-click>Identify the vulnerable package and affected version(s)</li>
  <li v-click>Review the changelog and release notes for the latest version</li>
  <li v-click>Assess breaking changes and update code as needed</li>
  <li v-click>Update the package to the latest secure version (including major upgrade if required)</li>
  <li v-click>Run tests to verify nothing is broken</li>
  <li v-click>Update the documentation to reflect the changes</li>
</ul>

<span v-click>Rinse and repeat for each package 🔁</span>

---
layout: center
---

<div style="text-align: center; max-width: 700px; margin: auto;">

# What if AI could help?

<br/>
If it's a repetitive task, it can be automated using a prompt.
</div>

---
layout: quote
background: '#1a1a0f'
---

🔐 Third-party tools check for CVEs and hand over to the agent to make the change

<span v-click style="display: block; margin-top: 2rem; font-weight: bold; color: #ffd700;">How do you give enough context on what to fix? How do you trust the fix?</span>

---
layout: three-cols
--- 

# Creating a workflow

::left::

**What is OSS doing:**

1. Daily checks of the codebases and packages
2. Create recommendations and vulnerability reports

::center::

**What is the agent doing:**

1. Reads the OSS report
2. Retrieves patch notes, migration guides etc and document choices
3. Flags and handles potential breaking changes
4. Delivers a plan for a **safe upgrade path**

::right::

**The human check:**

1. Checks the implementation plan
2. Review the upgrades and changes

---
layout: center
---

# Implementation

Multiple ways to implement this workflows, depending on tools availables: 

- Use MCP (if available)
- Use a skill that connects the agent to your thrid party tool (REST / CLI)
- Have the 3rd party tool open issues on GitHub, assigned to Copilot

---
layout: two-cols-header
---

# How it was implemented

::left::

❌ MCP not available

❌ Background or Cloud agents

::right::

✅ Custom skill using Snyk CLI

✅ Custom upgrade prompt per package manager

✅ Custom orchestration prompt

✅ Running locally on multiple chats

---
layout: three-cols
---

# Key takeaways
Learnings

Focus on what you can do with the tools that you have access to

AI is not just for coding, but also for other "development" activities

Advocate and drive adoption

---
layout: default
---

# Going further

How to refine and improve the workflow?

Handle different stacks (pip, Maven, Gradle)

Handle package overrides

Shift to GitHub Issues assigned to Copilot


---
layout: cover
---

# Observability

Dealing with bugs

_...or at least showing it's not your fault and passing it to another team_

---
layout: default
---

# Problems

Production bugs have to be investigated fast

The users will give close to no information

---
layout: default
---

# 🔍 Investigation

1. Ask user for more details:
   - Timeframe
   - What was the user trying to do
2. Check the logs for anomalies
3. Check error logs
4. Check traces

<div style="display: flex; justify-content: center; margin: 1.5rem 0;">
  <img src="/assets/datadog-logs.png" alt="Datadog trace example" style="max-width: 70%; border-radius: 8px; box-shadow: 0 2px 8px #0003;" />
  <img src="/assets/datadog-trace.png" alt="Datadog trace example" style="max-width: 70%; border-radius: 8px; box-shadow: 0 2px 8px #0003;" />
</div>


---
layout: center
---

<div style="text-align: center; max-width: 700px; margin: auto;">

# What if AI could help?

<br/>
If it's a repetitive task, at least for the initial analysis, it can be automated
</div>

---
layout: three-cols
--- 

# Creating a workflow

::left::

**What is the 3rd party tool:**

1. Collecting logs
2. Tracking errors
3. Displaying traces

::center::

**What is the agent doing:**

1. Reading the logs
2. Matching the logs with the codebase
3. Identifying the scenario
4. Delivers a possible list of scenarios
5. (optional) Plan to fix

::right::

**The human check:**

1. Review scenarios
2. Suggest fix
3. Handover ("it's not my service")
