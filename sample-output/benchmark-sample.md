# LLM Benchmark Report

**Run:** May 15, 2026 at 09:14 AM  
**Models:** claude-sonnet, claude-haiku, gemma, mistral  
**Tasks:** summarize, priorities, classify, draft

> Same prompts. Same data. Every model. Raw output below.

---

## Speed Summary

> **Time** = seconds to respond. Slower = less usable in real-time contexts.  
> **Tokens out** = a proxy for how much the model wrote. More isn't always better.

| Model | Task | Time | Tokens/sec | Tokens out |
|-------|------|-----:|-----------:|-----------:|
| claude-sonnet | summarize | 2.4s | 47.2 | 113 |
| claude-sonnet | priorities | 1.9s | 51.6 | 98 |
| claude-sonnet | classify | 2.1s | 44.8 | 94 |
| claude-sonnet | draft | 1.8s | 49.3 | 89 |
| claude-haiku | summarize | 1.1s | 68.4 | 75 |
| claude-haiku | priorities | 0.9s | 72.1 | 65 |
| claude-haiku | classify | 1.0s | 70.5 | 71 |
| claude-haiku | draft | 0.8s | 74.3 | 59 |
| gemma | summarize | 4.2s | 28.6 | 120 |
| gemma | priorities | 3.8s | 31.2 | 118 |
| gemma | classify | 5.1s | 24.9 | 127 |
| gemma | draft | 3.5s | 33.1 | 116 |
| mistral | summarize | 6.1s | 19.4 | 118 |
| mistral | priorities | 5.8s | 21.7 | 126 |
| mistral | classify | 7.3s | 16.2 | 118 |
| mistral | draft | 5.4s | 22.8 | 123 |

---

## Outputs — Side by Side

> Read down each section to compare the same answer from every model.

### summarize — Summarize a list of open items into a short digest

**Prompt:** `Write a 3-sentence summary of what needs attention this week...`

**claude-sonnet** — 2.4s — 113 tokens

```
This Week's Priorities:

1. Client & Team: Follow up on Tuesday's proposal, schedule onboarding call for new team member (starts Monday).
2. Deadlines: Review Q1 budget draft before Thursday meeting, respond to 3 urgent support tickets.
3. Project Health: Update timeline to reflect milestone 2 slip (4 days behind).
```

**claude-haiku** — 1.1s — 75 tokens

```
Three urgent items need immediate attention: respond to the 3 urgent support tickets, follow up on Tuesday's client proposal, and review the Q1 budget draft before Thursday. The project timeline also needs updating — milestone 2 has slipped 4 days. Additionally, the onboarding call for Monday's new team member still needs to be scheduled.
```

**gemma** — 4.2s — 120 tokens

```
This week requires attention to several pressing matters. First, follow up with the client regarding the Tuesday proposal and prepare for the Thursday Q1 budget review meeting. Additionally, three urgent support tickets need immediate responses, the project timeline requires updating due to a 4-day milestone 2 slip, and an onboarding call must be scheduled for the new team member starting Monday.
```

**mistral** — 6.1s — 118 tokens

```
There are several important items requiring attention this week. The most time-sensitive include following up on Tuesday's client proposal, reviewing the Q1 budget draft prior to Thursday's meeting, and addressing three urgent support tickets. Additionally, the project timeline needs to be updated to reflect the 4-day delay in milestone 2, and an onboarding call should be scheduled for the new team member beginning Monday.
```

---

### priorities — Extract the top 3 urgent items

**Prompt:** `List the 3 most urgent items from the list below. One sentence each. Be specific...`

**claude-sonnet** — 1.9s — 98 tokens

```
1. Respond to 3 urgent support tickets — these are already flagged urgent and likely customer-facing.
2. Review Q1 budget draft before Thursday — hard deadline, meeting already scheduled.
3. Follow up with client on Tuesday's proposal — time-sensitive, client is waiting.
```

**claude-haiku** — 0.9s — 65 tokens

```
1. Respond to 3 urgent support tickets — already marked urgent, likely blocking customers.
2. Review Q1 budget draft — Thursday meeting is a hard deadline.
3. Follow up on Tuesday's client proposal — client is waiting, opportunity at risk.
```

**gemma** — 3.8s — 118 tokens

```
1. Respond to 3 support tickets marked urgent — these are flagged as high priority and should be addressed immediately to maintain customer satisfaction and service standards.
2. Review Q1 budget draft before Thursday meeting — this has a firm deadline and needs to be completed before the scheduled meeting to allow for any necessary revisions.
3. Follow up with client on proposal sent Tuesday — timely follow-up is essential to maintain the client relationship and advance the sales process.
```

**mistral** — 5.8s — 126 tokens

```
1. Respond to 3 support tickets marked urgent — These are already flagged as requiring immediate attention and failing to address them could result in escalations or customer dissatisfaction.
2. Review Q1 budget draft before Thursday meeting — This has a firm deadline tied to a scheduled meeting, and timely review is necessary to ensure productive discussion and decision-making.
3. Follow up with client on proposal sent Tuesday — A prompt follow-up is important for maintaining momentum in the sales process and demonstrating responsiveness to the client.
```

---

### classify — Classify items by type and urgency

**Prompt:** `Return ONLY valid JSON. Classify each item below as an object with keys: item, type, urgency...`

**claude-sonnet** — 2.1s — 94 tokens

```json
[
  {"item": "Follow up with client on proposal sent Tuesday", "type": "client", "urgency": "high"},
  {"item": "Review Q1 budget draft before Thursday meeting", "type": "finance", "urgency": "high"},
  {"item": "Respond to 3 support tickets marked urgent", "type": "ops", "urgency": "high"},
  {"item": "Update project timeline — milestone 2 slipped by 4 days", "type": "ops", "urgency": "medium"},
  {"item": "Schedule onboarding call for new team member starting Monday", "type": "people", "urgency": "medium"}
]
```

**claude-haiku** — 1.0s — 71 tokens

```json
[
  {"item": "Follow up with client on proposal", "type": "client", "urgency": "high"},
  {"item": "Review Q1 budget draft", "type": "finance", "urgency": "high"},
  {"item": "Respond to 3 urgent support tickets", "type": "ops", "urgency": "high"},
  {"item": "Update project timeline", "type": "ops", "urgency": "medium"},
  {"item": "Schedule onboarding call", "type": "people", "urgency": "medium"}
]
```

**gemma** — 5.1s — 127 tokens

```json
[
  {"item": "Follow up with client on proposal sent Tuesday", "type": "client", "urgency": "high"},
  {"item": "Review Q1 budget draft before Thursday meeting", "type": "finance", "urgency": "high"},
  {"item": "Respond to 3 support tickets marked urgent", "type": "ops", "urgency": "high"},
  {"item": "Update project timeline — milestone 2 slipped by 4 days", "type": "ops", "urgency": "high"},
  {"item": "Schedule onboarding call for new team member starting Monday", "type": "people", "urgency": "medium"}
]
```

**mistral** — 7.3s — 118 tokens

```
Here is the JSON classification of the items:

[
  {"item": "Follow up with client on proposal sent Tuesday", "type": "client", "urgency": "high"},
  {"item": "Review Q1 budget draft before Thursday meeting", "type": "finance", "urgency": "high"},
  {"item": "Respond to 3 support tickets marked urgent", "type": "ops", "urgency": "high"},
  {"item": "Update project timeline", "type": "ops", "urgency": "medium"},
  {"item": "Schedule onboarding call for new team member", "type": "people", "urgency": "low"}
]

Note: I've classified the items based on the information provided.
```

---

### draft — Draft a short message based on context

**Prompt:** `Draft a 2-3 sentence Slack message to the team flagging the most urgent issue...`

**claude-sonnet** — 1.8s — 89 tokens

```
Hey team — heads up, we have 3 support tickets flagged urgent that need responses today. If you have bandwidth, please take a look and claim one. Client-facing items take priority this week.
```

**claude-haiku** — 0.8s — 59 tokens

```
Hey team, we've got 3 urgent support tickets that need attention today — please take a look when you get a chance. Client-facing issues are the priority right now. Thanks.
```

**gemma** — 3.5s — 116 tokens

```
Hi team, I wanted to bring to your attention that we currently have three support tickets that have been marked as urgent and require immediate attention. Addressing these promptly is crucial to maintaining our high standards of customer service and ensuring client satisfaction. Please prioritize reviewing and resolving these tickets as soon as possible. Thank you for your continued dedication and hard work.
```

**mistral** — 5.4s — 123 tokens

```
Hello team, I want to draw your attention to three support tickets that have been marked as urgent. These tickets require our immediate attention to ensure we maintain our high level of customer service and resolve any issues as quickly as possible. Please prioritize these tickets and provide timely and effective responses to address the customers' concerns.
```

---

*Generated with [llm-benchmark](https://github.com/devonclemente/llm-benchmark) — see the full story on [Medium](https://medium.com/@devonclemente/local-vs-cloud-llm-benchmark-ops-data-be4e0f93b46e)*
