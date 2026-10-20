# sandtable leaderboard results

The full results behind the [sandtable](https://github.com/sandtable-ai/sandtable) leaderboards: every conversation, tool call, check and token count. Every number on a board can be traced to a stored trial here, and re-checked without calling a model.

## freight-v1 (October 2026)

Thirteen models play the agent on a fictional freight brokerage's carrier-sales desk: 50 rehearsed calls, four trials each, the same simulated caller for every model, deterministic grading.

- **Board:** [`freight-v1/LEADERBOARD.md`](freight-v1/LEADERBOARD.md) ([HTML](https://sandtable-ai.github.io/leaderboard/freight-v1/leaderboard.html), with links to each model's report)
- **Methodology:** [sandtable.dev/leaderboard](https://sandtable.dev/leaderboard). It covers how the board was run, what is graded and what it can't see.
- **Config:** [`freight-v1/models.yaml`](freight-v1/models.yaml), the exact models file the board ran with

Each model has a folder:

| File | What it holds |
|---|---|
| `run.json` | the agent spec and effort, and the sandtable version, commit, provider and region its trials ran with |
| `results.json` | every trial: the conversation, each tool call with its arguments and result, the world's changes, every check with its verdict, and token usage and cost |
| `report.html` | the same trials as a self-contained report you can read in a browser |

`leaderboard.json` holds the ranked rows and the sandtable commit that graded them.

## Check the grading yourself

Grading needs no model, so anyone can re-score the stored trials under the freight domain's rules:

```bash
git clone https://github.com/sandtable-ai/sandtable && cd sandtable
git checkout 90e6e2d   # the grading commit recorded in freight-v1/leaderboard.json
npm ci
node src/cli.ts regrade ../leaderboard/freight-v1/claude-opus-5-5/results.json -d examples/freight -o /tmp/regraded
```

`regrade` replays each trial's tool calls against a fresh copy of the world, so it refuses if the stored results no longer match what the domain would return. Any verdict it changes is printed.

To rerun the board itself, with model calls and your own credentials, see the methodology page's "Reproduce" section.

## License

The results are released under [CC BY 4.0](LICENSE). Every company, person, load and number in them is fictional.
