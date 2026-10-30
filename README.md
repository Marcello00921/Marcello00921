### Marcello Zamproni · applied AI (agent systems, evaluation and deployment)

I run a one-person company in which a growing share of functions is handed to teams of AI agents, and most of my attention goes to the layer that decides whether their work counts. The pattern keeps repeating: I look for the defect in the model and find it in my own measurement. Each time I write down the number, the date and the cause, and the next piece of work is checked against that record.

#### How work closes

A code change in my work queue closes only when the check failed before the change, a negative control still fails on a known-wrong solution, and two narrow verifiers in a clean context accept the evidence (an arbiter steps in on disagreement): 566 of 579 since late September 2026, the rest through a logged exception or a lighter mechanical check.

On a 24-task harness, a single agent got the verdict right on 17 of 24 (four false greens, three false reds); the supervised arm 45 of 48 over two runs (three false greens). The supervised arm was tuned on those same tasks, and on four untouched blind tasks both arms solved everything, so I read it as a direction, not proof.

#### Open-source Claude Code tools

| repo | what it does |
|---|---|
| [cc-output-cap](https://github.com/Marcello00921/cc-output-cap) | hook that trims large tool output to head and tail, full output on disk |
| [cc-run-detached](https://github.com/Marcello00921/cc-run-detached) | runs long commands detached, state in a file, checked with short calls |
| [cc-windows-guards](https://github.com/Marcello00921/cc-windows-guards) | `PreToolUse` guards against recursive deletes and kill-by-name |

The same setup, written up for Brazilian developers: [Claude Code field guide (PT-BR)](https://guia-claude-code-8r2.pages.dev/).

#### Dataset

[Agent Verdict Bench (PT-BR)](https://huggingface.co/datasets/mASMK2/agent-verdict-bench-ptbr): 14 short engineering tasks where a coding agent tends to say "done" when it is not, each with a deterministic verifier and a known-wrong solution that must fail.

#### Other measured work

- **Model choice by a rule written before the run.** 48 task-paired runs: Opus 5.5 reached the correct verdict 45/48 with 3 false greens, Sonnet 5.5 40/48 with 7. The verifier role stayed on Opus because false greens were the hard barrier; the accuracy gap sits at the edge of noise (McNemar exact p = 0.062) and is reported that way.
- **The defect was in my evaluation code, not the model.** Benchmarking four multi-object trackers, the failures came from a position-drift bug in my own harness; fixing the measurement moved stable-track rate from 6/12 to 14/16 on the same tracker.
- **A system that refuses instead of promising.** In a computer-vision archive (82 hours of footage, 70,997 registered vehicles), 93% of records asserted vehicle colour while none stored one; every record written since carries an explicit refusal and its reason.
- **Video that shows what the sentence says.** A scene director builds a custom animation per narration beat; beats whose middle frame shows what the sentence says rose from 8/26 to 24/26 on the first topic, confirmed by a blind re-judge.
- **voiceval** (about 400 lines with tests) fails a CI build when a voice agent misreads a number, name or entity.

#### Standards

National Expert, Brazilian AI committee (ABNT/CB-021/CE 021 005 042).

**Stack:** Python, FastAPI, Postgres/Supabase, React/TypeScript/Vite, Claude Code subagents and workflows, RF-DETR, OWLv2, OC-SORT, PPO, GNNs, real-time speech-to-speech.

[LinkedIn](https://linkedin.com/in/marcellozamproni) · [Hugging Face](https://huggingface.co/mASMK2) · Campo Grande, Brazil · São Paulo hybrid, open to relocation
