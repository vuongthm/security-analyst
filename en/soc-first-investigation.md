---
id: "field-notes:soc-first-investigation"
translationKey: "field-notes:soc-first-investigation"
title: "SOC: from an alert to a hypothesis"
description: "Separate signals, evidence, and conclusions when learning security analysis."
topics: ["soc", "security"]
tags: ["soc", "security"]
date: "2026-11-03"
kind: "guide"
level: "beginner"
featured: true
---

## An alert is a starting point

An alert does not automatically mean an attack. It means a configured condition was met. The next step is to establish context and test a hypothesis.

## The first five questions

1. Which account or device is involved?
2. When did it happen, and in which time zone?
3. Which data supports the alert?
4. What baseline makes the behavior unusual?
5. What additional evidence would help?

## Build a timeline

Order authentication, application access, and network events by time. Normalize time zones before correlation. Preserve original records and document filters and data sources.

```text
09:12 UTC  authentication failure
09:14 UTC  authentication success
09:16 UTC  new remote session
```

This illustrative sequence is not sufficient to conclude that an account is compromised.

## Write a bounded conclusion

Separate observations, inferences, and unknowns. Record why the alert was closed or escalated. A good report lets another person reconstruct how you reached the conclusion.

## Further reading

[MITRE ATT&CK](https://attack.mitre.org/) provides shared language for tactics and techniques. Use a framework to organize evidence, not to replace it.

```quiz
{
  "title": "Check your understanding",
  "questions": [
    {
      "id": "q1",
      "question": "What does an alert alone establish?",
      "options": [
        "A configured detection condition was triggered",
        "A confirmed intrusion occurred",
        "An account is definitely compromised"
      ],
      "answer": 0,
      "explanation": "Context and corroborating evidence are needed before declaring an incident."
    },
    {
      "id": "q2",
      "question": "What matters before combining logs into a timeline?",
      "options": [
        "Delete records contradicting the hypothesis",
        "Keep only red rows",
        "Normalize time zones and retain source data"
      ],
      "answer": 2,
      "explanation": "Inconsistent time zones can reverse event order; original logs enable verification."
    }
  ]
}
```
