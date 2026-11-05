---
id: "soc-notes:junior-security-analyst-intro"
translationKey: "soc-notes:junior-security-analyst-intro"
title: "Junior Security Analyst Intro"
description: "Distinguish alerts, events and incidents, then begin triage with evidence."
topics: ["soc"]
tags: ["soc", "blue-team", "soc-level-1"]
date: "2026-11-05"
kind: guide
level: beginner
weight: 0
learning:
  path: soc-level-1
  section: blue-team-introduction
  step: junior-security-analyst-intro
---

## One role, several sources of evidence

A SOC brings together people, processes and tools to monitor and respond to security events. A junior analyst often begins with triage: checking an alert, establishing context, recording evidence and escalating through the team's workflow.

A SIEM can aggregate events across systems, while EDR provides endpoint visibility. Their views complement each other; a dashboard does not replace an investigation.

## An alert is not a verdict

Consider repeated failed logins followed by a success from a new address. This warrants investigation, but does not establish account compromise by itself. Correlate time, device, user history, MFA and related logs.

Keep separate notes for observations, hypotheses and missing evidence. Retain original logs and record filters so another analyst can reproduce the analysis.

## Keep triage within its scope

Identify the affected assets and identities, check data completeness and time zones, assess impact and signal confidence, and document the reason for closure or escalation. Production containment requires the appropriate authority and workflow.

## References

- [NIST SP 800-61 Rev. 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final)
- [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/soclevel1)

```quiz
{
  "title": "Check your understanding",
  "questions": [
    {
      "id": "q1",
      "question": "What helps triage before reaching a conclusion?",
      "options": [
        "Correlate assets, time and relevant evidence",
        "Block every host as soon as an alert appears",
        "Treat the alert as final proof"
      ],
      "answer": 0,
      "explanation": "Triage establishes context and evaluates signal confidence."
    },
    {
      "id": "q2",
      "question": "How do SIEM and EDR relate?",
      "options": [
        "They provide complementary views",
        "They are two names for one log type",
        "EDR replaces every network log source"
      ],
      "answer": 0,
      "explanation": "SIEM aggregates events while EDR focuses on endpoint activity."
    },
    {
      "id": "q3",
      "question": "What should an analysis note separate?",
      "options": [
        "Observations, hypotheses and missing information",
        "Only tool names and operators",
        "Only confident conclusions"
      ],
      "answer": 0,
      "explanation": "Separating evidence from inference helps colleagues verify and continue the investigation."
    }
  ]
}
```
