---
id: "soc-notes:humans-as-attack-vectors"
translationKey: "soc-notes:humans-as-attack-vectors"
title: "Humans as Attack Vectors"
description: "Examine phishing and identity abuse in context without blaming users."
topics: ["soc"]
tags: ["soc", "blue-team", "soc-level-1"]
date: "2026-11-05"
kind: guide
level: beginner
weight: 2
learning:
  path: soc-level-1
  section: blue-team-introduction
  step: humans-as-attack-vectors
---

## An attack may start with a request

A message, login invitation or support request can exploit trust and time pressure. An alert involving an account is not proof that its owner acted negligently.

## Examine the message in context

Preserve the original message and relevant details through the organization's workflow. Check sender information, routing, destination links and the requested action. Familiar display names and logos are not proof of authenticity.

Do not open suspicious links on a daily-use device merely to validate them. Use the approved analysis process and environment.

## Correlate identity evidence

Compare authentication, MFA, device and timing records. An unfamiliar IP may reflect a VPN or travel; establish context before reaching a conclusion.

## Defense needs several layers

Training and an accessible reporting channel work alongside least privilege, identity protections and detection. Capture what helped someone notice a suspicious request and improve the process rather than assigning blame.

## References

- [NIST SP 800-61 Rev. 3](https://csrc.nist.gov/pubs/sp/800/61/r3/final)
- [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/soclevel1)

```quiz
{
  "title": "Check your understanding",
  "questions": [
    {
      "id": "q1",
      "question": "Does a familiar display name prove an email is authentic?",
      "options": [
        "Yes, display names cannot be spoofed",
        "Yes, if the logo looks professional",
        "No, check context and sender information"
      ],
      "answer": 2,
      "explanation": "Display names and imagery can be copied."
    },
    {
      "id": "q2",
      "question": "Which approach fits the note for analyzing a suspicious link?",
      "options": [
        "Use the approved analysis process and environment",
        "Open it immediately on a daily-use device",
        "Share credentials to check it"
      ],
      "answer": 0,
      "explanation": "Collect evidence without exposing a daily-use device to unnecessary risk."
    },
    {
      "id": "q3",
      "question": "How should an unfamiliar login IP be interpreted?",
      "options": [
        "A signal requiring context such as VPN use or travel",
        "Definite proof the user is at fault",
        "A reason to discard other logs"
      ],
      "answer": 0,
      "explanation": "Correlate MFA, device and timing evidence to test the hypothesis."
    }
  ]
}
```
