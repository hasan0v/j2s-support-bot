# Evaluation plan

J2S must be evaluated as a support workflow, not only as a text generator. A useful answer must be grounded in the approved knowledge base, safe, timely, and easy to escalate when automation is insufficient.

## Evaluation set

Build a versioned set of representative support questions with:

- the expected answer or required evidence;
- the relevant knowledge-base source;
- the expected route, escalation, or refusal;
- difficulty and topic labels;
- adversarial and out-of-scope examples.

Keep authoring examples separate from the held-out reporting set.

## Metrics

| Layer | Metric |
|---|---|
| Retrieval | Recall@k and mean reciprocal rank for the expected source |
| Grounding | Supported-claim rate and citation/source correctness |
| Answer quality | Human-rated correctness, completeness, and clarity |
| Safety | Prompt-injection success rate, sensitive-data disclosure, unsafe-action rate |
| Workflow | Correct escalation, containment, and routing rate |
| Operations | Median and p95 latency, cost per resolved request, error and timeout rate |

## Required slices

- answerable versus unanswerable questions;
- current versus deliberately stale knowledge;
- short and multi-turn conversations;
- web widget versus SMS constraints;
- direct prompt injection and retrieved-content injection;
- English and supported local-language queries.

## Human review

Reviewers should score outputs without seeing the model name. Disagreements must be adjudicated and added to the error taxonomy. Do not report a single quality percentage without the rubric, sample size, model, prompt version, and knowledge-base version.

## Release gate

1. Backend syntax and both frontend builds pass.
2. Authentication and administrator routes reject unauthorized access.
3. Out-of-scope questions reliably escalate or refuse.
4. Retrieved untrusted text cannot override system rules.
5. Known limitations and the evaluated configuration are published.

## Current evidence status

The repository contains architecture and guardrail documentation, but it does not yet include a reproducible benchmark report. Current descriptions therefore claim implemented capabilities only. The next milestone is an automated retrieval and response evaluation harness.
