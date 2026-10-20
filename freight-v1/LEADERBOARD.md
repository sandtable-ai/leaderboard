# Leaderboard: freight-carrier-sales

Each model plays the agent on every task 4 times, against the same simulated callers (bedrock:global.anthropic.claude-sonnet-5-5). pass^4 is the share of tasks where all 4 trials passed. Grading is deterministic: end state, rules checked on every tool call and message, required and forbidden tools. Soft rules never fail a trial: each shows how often the model broke it, in the trials where it applied. Cost / trial counts the agent's model only; leaderboard.json also has the cost with the simulated caller.

| # | Model | pass^1 | pass^4 | Rule violations | Top failure | Soft rules | Cost / trial | p95 turn |
|---|---|---|---|---|---|---|---|---|
| 1 | Claude Opus 5.5 (effort medium) | 100.0% | 100.0% | 0 |  | counter-at-ceiling 23.2% (13/56) | $0.044 | 6.5s |
| 2 | Claude Sonnet 5.5 (effort high) | 100.0% | 100.0% | 0 |  | counter-at-ceiling 18.5% (10/54) | $0.021 | 4.9s |
| 3 | Claude Haiku 5.5 (effort medium) | 100.0% | 100.0% | 0 |  | counter-at-ceiling 7.8% (4/51) | $0.0013 | 4.9s |
| 4 | GPT-6 Astra | 100.0% | 100.0% | 0 |  | counter-at-ceiling 13.7% (7/51) | $0.040 | 4.4s |
| 5 | GPT-6.1 Sol | 100.0% | 100.0% | 0 |  | counter-at-ceiling 19.6% (10/51) | $0.0062 | 5.7s |
| 6 | Grok 4.7 | 100.0% | 100.0% | 0 |  | counter-at-ceiling 26.4% (14/53) | $0.026 | 15.7s |
| 7 | GPT-6 Luna | 99.0% | 96.0% | 1 | state:bookings#2 (2×) | counter-at-ceiling 30.2% (16/53) | $0.0005 | 2.9s |
| 8 | MiniMax M2.5 | 75.5% | 64.0% | 47 | never-disclose-ceiling (45×) | counter-at-ceiling 46.7% (14/30) | $0.012 | 14.8s |
| 9 | Qwen3 Next 80B | 56.5% | 46.0% | 74 | never-disclose-ceiling (67×) | counter-at-ceiling 92.3% (12/13) | $0.0043 | 4.2s |
| 10 | gpt-oss-120b | 59.0% | 40.0% | 71 | never-disclose-ceiling (71×) | counter-at-ceiling 90.2% (37/41) | $0.0040 | 4.4s |
| 11 | Nova 2 Lite | 52.0% | 36.0% | 100 | never-disclose-ceiling (73×) | counter-at-ceiling 66.7% (10/15) | $0.0032 | 2.8s |
| 12 | Ministral 3 14B | 64.0% | 34.0% | 69 | never-disclose-ceiling (31×) | counter-at-ceiling 40.4% (19/47) | $0.0052 | 8.7s |
|  | _Do-nothing baseline_ | 32.0% | 32.0% | 0 | state:bookings#1 (20×) | counter-at-ceiling n/a | n/a | 0.0s |
| 13 | Nemotron 3 Super 120B | 44.5% | 30.0% | 115 | never-disclose-ceiling (104×) | counter-at-ceiling 80.0% (16/20) | $0.0060 | 3.8s |

Generated 2026-10-20T12:39:43.145Z with [sandtable](https://github.com/sandtable-ai/sandtable) 0.1.0-alpha.1 (commit 90e6e2d). Per-model reports and trajectories are in the folders next to this file.
