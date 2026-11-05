---
id: "soc-notes:systems-as-attack-vectors"
translationKey: "soc-notes:systems-as-attack-vectors"
title: "Systems as Attack Vectors"
description: "Connect assets, configuration and telemetry to understand system exposure."
topics: ["soc"]
tags: ["soc", "blue-team", "soc-level-1"]
date: "2026-11-05"
kind: guide
level: beginner
weight: 3
learning:
  path: soc-level-1
  section: blue-team-introduction
  step: systems-as-attack-vectors
---

## Understand the system before the alert

An exposed service, excessive permissions or unpatched software may create an entry point. Impact depends on assets, data, privileges and connections to other components.

## Map the available visibility

For a small application, record exposed services, administrative identities, collected logs and ownership. Combine network observations with endpoint behavior: SIEM and EDR provide different views.

## A vulnerability is not proof of exploitation

Version information or a scan result is an investigative lead. Incident analysis needs corroboration, such as unusual processes, file changes, authentication activity and related connections. Absence of an observation can also mean missing telemetry.

## Prioritize actual risk

Consider exposure, privileges and business impact. Remediation requires ownership, controlled changes and verification. Keep collection within the authorized scope and retain necessary evidence.

## References

- [NIST SP 800-61 Rev. 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final)
- [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/soclevel1)

```quiz
{
  "title": "Check your understanding",
  "questions": [
    {
      "id": "q1",
      "question": "What does finding a vulnerable version establish by itself?",
      "options": [
        "An investigative risk lead requiring corroboration",
        "The system was definitely exploited",
        "Logs are no longer needed"
      ],
      "answer": 0,
      "explanation": "Vulnerability status and evidence of exploitation are different questions."
    },
    {
      "id": "q2",
      "question": "What can absence of a behavior in logs mean?",
      "options": [
        "The SIEM is definitely disabled",
        "Visibility may be missing; absence alone does not settle what happened",
        "The system is definitely safe"
      ],
      "answer": 1,
      "explanation": "Check collection coverage and data completeness."
    },
    {
      "id": "q3",
      "question": "What should remediation priority consider?",
      "options": [
        "Only the security product name",
        "Exposure, privileges and business impact",
        "Only the number of screenshots"
      ],
      "answer": 1,
      "explanation": "Risk is contextual; changes need ownership and verification."
    }
  ]
}
```
