---
id: "soc-notes:soc-role-in-blue-team"
translationKey: "soc-notes:soc-role-in-blue-team"
title: "SOC Role in Blue Team"
description: "Understand how the SOC works with incident response, system owners and threat intelligence."
topics: ["soc"]
tags: ["soc", "blue-team", "soc-level-1"]
date: "2026-11-05"
kind: guide
level: beginner
weight: 1
learning:
  path: soc-level-1
  section: blue-team-introduction
  step: soc-role-in-blue-team
---

## Blue Team extends beyond monitoring

Blue Team describes defensive activities. A SOC focuses on monitoring and analysis, but works with infrastructure operations, identity administrators, incident responders and asset owners. Responsibilities vary by organization.

An alert may begin in a SIEM, gain endpoint context from EDR and then be escalated to the appropriate incident coordinator. Clear communication prevents uncoordinated changes to the same system.

## Escalate a useful evidence package

Include the asset, time and time zone, relevant evidence, possible impact, checks already performed and the question the next team needs to answer. Priority needs a rationale beyond a red label on a dashboard.

## Improve after investigating

Noisy detections can be tuned through change control. Missing telemetry should be documented. Repeatable tasks can become workbooks with conditions and ownership. These improvements make subsequent investigations more reproducible.

## References

- [NIST SP 800-61 Rev. 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final)
- [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/soclevel1)

```quiz
{
  "title": "Check your understanding",
  "questions": [
    {
      "id": "q1",
      "question": "Is Blue Team synonymous only with the SOC?",
      "options": [
        "Yes, operations teams are unnecessary",
        "No, it includes other defensive roles and system owners",
        "Yes, everything happens in one dashboard"
      ],
      "answer": 1,
      "explanation": "A SOC collaborates with other teams; responsibilities depend on the organization."
    },
    {
      "id": "q2",
      "question": "What belongs in an escalation package?",
      "options": [
        "Only the claim: a hacker exists",
        "Evidence, possible impact and checks already performed",
        "Only a red alert screenshot"
      ],
      "answer": 1,
      "explanation": "This lets the next team continue without reconstructing context from guesses."
    },
    {
      "id": "q3",
      "question": "What is a useful response to a noisy rule?",
      "options": [
        "Review and tune it through change control",
        "Silently remove the entire log source",
        "Treat every alert as an incident"
      ],
      "answer": 0,
      "explanation": "Tuning should preserve useful detection and include verification."
    }
  ]
}
```
