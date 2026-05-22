# Evals (evals)

A landscape catalog of the platforms, frameworks, libraries, and benchmark suites used to evaluate large language models, LLM-based applications, and AI agents. The topic spans human-rated, LLM-as-a-judge, reference-based, reference-free, and benchmark-aligned approaches to measuring AI system quality. Tracked alongside the eval platforms are the canonical multi-task and code/agent benchmark suites (MMLU, HumanEval, GAIA, AgentBench, BIG-Bench) that establish public points of comparison.

**URL:** [https://github.com/api-evangelist/evals](https://github.com/api-evangelist/evals)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=topic-evals&utm_content=repo)

## Tags

Evals, LLM Evaluation, AI Quality, Benchmarks, LLM as a Judge, Observability, Agent Evaluation, RAG Evaluation, Test-Driven AI

## Timestamps

- **Created:** 2026-05-22
- **Modified:** 2026-05-22

## The Eval Landscape

The eval space is organized along two axes: **what is being scored** (single-turn output vs. agent trajectory vs. RAG pipeline) and **how it is being scored**. The "how" axis has settled into five recognizable modes:

| Mode | What it is | Where it shines | Where it struggles |
|---|---|---|---|
| **Human-Rated** | Domain experts or end users rate outputs (Likert, thumbs, free text) | Ground truth, final acceptance, judge calibration | Slow, expensive, inconsistent at scale |
| **Reference-Based** | Output compared to a known-correct answer via exact match, BLEU/ROUGE, embedding similarity, or `pass@k` | Benchmarks (MMLU, HumanEval), classification, code | Free-form text where many correct answers exist |
| **Reference-Free** | Output scored against a criterion (faithfulness, toxicity, coherence) without ground truth | Production traffic, online monitoring, RAG triad | Subjective criteria, judge drift |
| **LLM-as-a-Judge** | A second LLM applies a written rubric to score the output | Free-form text, RAG, agents — the modern default | Judge bias, cost, calibration to humans |
| **Benchmark-Aligned** | Run against a standardized public dataset (MMLU, HumanEval, GAIA, AgentBench, BIG-Bench) | Cross-model comparison, leaderboards, marketing | Contamination, narrow coverage, gameable |

Most production eval programs combine modes: reference-based suites for components that have ground truth, LLM-as-a-judge plus reference-free scorers for free-form text, periodic human-rated sampling to calibrate judges, and a public benchmark battery for headline numbers.

## APIs

### OpenAI Evals

OpenAI Evals is the open-source framework released by OpenAI for evaluating large language models and LLM-based systems. The README states "Evals provide a framework for evaluating large language models (LLMs) or systems built using LLMs." The repo bundles a registry of benchmark evals, support for model-graded grading without writing custom code, private eval data via Snowflake logging, and templates for prompt chains and tool-using agents. Written primarily in Python, the project sits at roughly 18.5k stars / 3k forks.

**Human URL:** [https://github.com/openai/evals](https://github.com/openai/evals)

#### Tags

OpenAI, Open Source, Model Graded, Benchmark Registry, Python

#### Properties

- [GitHubRepository](https://github.com/openai/evals)
- [Documentation](https://github.com/openai/evals/tree/main/docs)
- [License](https://github.com/openai/evals/blob/main/LICENSE.md)

### Inspect AI

Inspect AI is an open-source framework for large language model evaluations developed and maintained by the UK AI Security Institute (UK AISI) and Meridian Labs. It supports text comparisons, model-based grading such as `model_graded_fact()`, and custom scorers. Datasets carry input and target columns, with multimodal support across image, audio, and video. The framework targets frontier-AI capability and safety assessment across coding, reasoning, knowledge, behavior, and multimodal understanding.

**Human URL:** [https://inspect.aisi.org.uk/](https://inspect.aisi.org.uk/)

#### Tags

UK AISI, Open Source, Frontier AI, Model Graded, Safety Evaluation

#### Properties

- [Documentation](https://inspect.aisi.org.uk/)
- [GitHubRepository](https://github.com/UKGovernmentBEIS/inspect_ai)

### Braintrust

Braintrust is a commercial evaluation platform that captures eval runs as immutable, comparable experiment snapshots. The product supports code-based scorers, built-in autoevals, and LLM-as-a-judge evaluators for both offline and production use. Datasets are collections of test cases (input, optional expected output, metadata) sourced from production logs, user feedback, or manual curation. Experiments slot into CI/CD pipelines to detect regressions "before they reach production."

**Human URL:** [https://www.braintrust.dev/](https://www.braintrust.dev/)

#### Tags

Commercial, LLM as a Judge, CI/CD, Experiments, Regression Detection

#### Properties

- [Documentation](https://www.braintrust.dev/docs)
- [EvaluationGuide](https://www.braintrust.dev/docs/guides/evals)
- [Pricing](https://www.braintrust.dev/pricing)

### LangSmith Evaluation

LangSmith Evaluation is LangChain's evaluation framework for measuring application quality across the lifecycle. The docs describe evals as "a way to breakdown what 'good' looks like and measure it." It supports code evaluators (deterministic rules), LLM-as-judge evaluators (reference-based or reference-free), and heuristic checks (length, latency, keywords). Concepts include datasets and examples, experiments, and pairwise evaluation for relative comparisons.

**Human URL:** [https://docs.langchain.com/langsmith/evaluation-concepts](https://docs.langchain.com/langsmith/evaluation-concepts)

#### Tags

LangChain, LLM as a Judge, Pairwise, Reference-Free, Online and Offline

#### Properties

- [Documentation](https://docs.langchain.com/langsmith/evaluation-concepts)
- [Portal](https://smith.langchain.com)
- [Pricing](https://www.langchain.com/pricing-langsmith)

### Promptfoo

Promptfoo is an open-source CLI and library for evaluating and red-teaming LLM applications. The docs describe it as enabling "test-driven LLM development rather than trial-and-error" and producing "matrix views that let you quickly evaluate outputs across many prompts." It supports assertion-based scoring, integrations across OpenAI, Anthropic, Azure, Google, HuggingFace, and open-source models, plus automated red-team and pentest runs that produce vulnerability and risk reports.

**Human URL:** [https://www.promptfoo.dev/](https://www.promptfoo.dev/)

#### Tags

Open Source, CLI, Red Teaming, Assertions, Test-Driven

#### Properties

- [Documentation](https://www.promptfoo.dev/docs/intro/)
- [GitHubRepository](https://github.com/promptfoo/promptfoo)
- [RedTeam](https://www.promptfoo.dev/docs/red-team/)

### Helicone

Helicone is an open-source observability and monitoring platform for LLM applications. The homepage states "The world's fastest-growing AI companies rely on Helicone to route, debug, and analyze their applications." Beyond observability dashboards (requests, segments, sessions, users), it offers prompt management, datasets, a playground, rate-limit tracking, and alerts. LLM-as-a-judge style evaluation runs against captured request logs.

**Human URL:** [https://www.helicone.ai/](https://www.helicone.ai/)

#### Tags

Open Source, Observability, Proxy, Prompt Management, Y Combinator

#### Properties

- [Documentation](https://docs.helicone.ai/)
- [GitHubRepository](https://github.com/Helicone/helicone)
- [Pricing](https://www.helicone.ai/pricing)

### Patronus AI

Patronus AI is a frontier lab building evaluation infrastructure and Digital World Models for human-aligned AGI. Its evaluator models include Lynx (a hallucination-detection model reported to outperform GPT-4 on hallucination tasks) and GLIDER (an evaluation model producing reasoning chains with explainable judgments). Coverage spans research science, software development, customer service, product applications, finance, and multi-turn dialogue / long-horizon task planning.

**Human URL:** [https://www.patronus.ai/](https://www.patronus.ai/)

#### Tags

Commercial, Hallucination Detection, Judge Models, Lynx, GLIDER

#### Properties

- [Documentation](https://docs.patronus.ai/)
- [Portal](https://app.patronus.ai)

### DeepEval (Confident AI)

DeepEval is an open-source LLM evaluation package, paired with Confident AI as the hosted observability/evals/monitoring tier. The docs call DeepEval "an open-source LLM eval package" and Confident AI "an AI quality platform with observability, evals, and monitoring." Metrics include GEval (research-backed custom metric), AnswerRelevancyMetric, TaskCompletionMetric, and ConversationalGEval. Test cases use LLMTestCase and ConversationalTestCase shapes; datasets organize Golden test cases for sync or async runs.

**Human URL:** [https://www.deepeval.com/](https://www.deepeval.com/)

#### Tags

Open Source, GEval, RAG, Conversational, Python

#### Properties

- [Documentation](https://www.deepeval.com/docs/getting-started)
- [GitHubRepository](https://github.com/confident-ai/deepeval)
- [Portal](https://app.confident-ai.com)

### Arize AI (Phoenix)

Arize AI provides an AI observability and evaluation platform centered on Arize AX (the commercial product) and Phoenix (open-source LLM tracing and evaluation). Phoenix runs LLM-as-a-judge evaluators across traces, supports datasets and experiments, and integrates with OpenTelemetry. Arize AX layers monitoring, drift detection, and root-cause analysis on top of model and LLM telemetry.

**Human URL:** [https://arize.com/](https://arize.com/)

#### Tags

Commercial, Open Source, Phoenix, OpenTelemetry, Observability

#### Properties

- [Documentation](https://arize.com/docs/ax/)
- [GitHubRepository](https://github.com/Arize-ai/phoenix)
- [Portal](https://app.arize.com)

### Galileo

Galileo is an enterprise AI observability and evaluation engineering platform. The product line emphasizes "20+ built-in evaluators" spanning RAG, agents, safety, and security, plus custom evaluators that "auto-tune metrics from live feedback." Luna refers to compact distilled evaluator models that "monitor 100% of your traffic at 97% lower cost." The homepage tagline reads "Don't just monitor AI failures. Stop them."

**Human URL:** [https://www.galileo.ai/](https://www.galileo.ai/)

#### Tags

Commercial, Enterprise, Luna, RAG, Safety

#### Properties

- [Documentation](https://docs.galileo.ai/)
- [Portal](https://app.galileo.ai)

### Humanloop

Humanloop was a development platform for LLM applications, describing itself as having been "the first development platform for LLM applications" and having "shaped industry standards for how to manage and evaluate AI." Following its acquisition by Anthropic the platform has been sunset, with a migration path published for former customers. Retained in this catalog for historical completeness.

**Human URL:** [https://humanloop.com/](https://humanloop.com/)

#### Tags

Historical, Acquired, Anthropic, Prompt Management

#### Properties

- [Documentation](https://humanloop.com/docs)
- [AcquisitionNotice](https://humanloop.com/)

### TruLens

TruLens is an open-source evaluation and tracing platform for AI agents that helps developers "move from vibes to metrics." Its feedback-function library covers the RAG triad — groundedness (responses supported by retrieved content), context relevance (retrieved documents match the query), and answer relevance (responses address the user question) — plus coherence, comprehensiveness, toxicity, sentiment, fairness, and custom metrics. Integrates with OpenTelemetry traces and any agent framework.

**Human URL:** [https://www.trulens.org/](https://www.trulens.org/)

#### Tags

Open Source, RAG Triad, Feedback Functions, Snowflake, OpenTelemetry

#### Properties

- [Documentation](https://www.trulens.org/)
- [GitHubRepository](https://github.com/truera/trulens)

### Weights and Biases Weave

W&B Weave is a platform for evaluating, monitoring, and iterating on AI agents and applications, started with "one line of code." Weave Evaluations enable visual comparison of runs, automatic versioning of datasets and scorers, an interactive playground, and leaderboards. Scorers include pre-built ones (toxicity, hallucination), custom Python scoring functions, human feedback collection, and third-party scorers from providers such as RAGAS and LangChain.

**Human URL:** [https://wandb.ai/site/weave](https://wandb.ai/site/weave)

#### Tags

Weights and Biases, Commercial, Scorers, Leaderboards, Human Feedback

#### Properties

- [Documentation](https://weave-docs.wandb.ai/)
- [GitHubRepository](https://github.com/wandb/weave)
- [Portal](https://wandb.ai)

### Ragas

Ragas is an open-source evaluation library focused on retrieval-augmented generation, described in its own docs as "a library that helps you move from 'vibe checks' to systematic evaluation loops for your AI applications." It exposes LLM-driven metrics for RAG (faithfulness, context recall, answer relevancy), integrates with LangChain and LlamaIndex, and supports custom metric authoring as a complement to other eval platforms (Weave, LangSmith).

**Human URL:** [https://docs.ragas.io/](https://docs.ragas.io/)

#### Tags

Open Source, RAG, Faithfulness, Context Recall, Library

#### Properties

- [Documentation](https://docs.ragas.io/en/stable/)
- [GitHubRepository](https://github.com/explodinggradients/ragas)

### MLflow LLM Evaluate

MLflow LLM evaluate extends MLflow's experiment tracking with `mlflow.evaluate()` support for LLM tasks. The API runs reference-based and reference-free metrics (toxicity, perplexity, BLEU, ROUGE, exact match, custom LLM judges) over a logged model or a function and persists results into MLflow's experiment store alongside traditional ML metrics. Sits inside the broader MLflow open-source project.

**Human URL:** [https://mlflow.org/](https://mlflow.org/)

#### Tags

Open Source, MLflow, Experiment Tracking, LLM Judges, Apache

#### Properties

- [Documentation](https://mlflow.org/docs/latest/llms/llm-evaluate/index.html)
- [GitHubRepository](https://github.com/mlflow/mlflow)

### MMLU Benchmark

MMLU (Measuring Massive Multitask Language Understanding) is a multiple-choice benchmark spanning 57 subjects from STEM and international law to nutrition and religion. It contains 15,908 multiple-choice questions (four options each), of which 1,540 are reserved for hyperparameter tuning. Per its overview, "It was one of the most commonly used benchmarks for comparing the capabilities of large language models, with over 100 million downloads as of July 2024."

**Human URL:** [https://github.com/hendrycks/test](https://github.com/hendrycks/test)

#### Tags

Benchmark, Knowledge, Multiple Choice, Multitask, Reference-Based

#### Properties

- [GitHubRepository](https://github.com/hendrycks/test)
- [Paper](https://arxiv.org/abs/2009.03300)
- [Dataset](https://huggingface.co/datasets/cais/mmlu)

### HumanEval Benchmark

HumanEval is OpenAI's evaluation harness for code-generation models, described in its README as "an evaluation harness for the HumanEval problem solving dataset described in the paper 'Evaluating Large Language Models Trained on Code'." Functional correctness is measured by executing model-generated code against unit tests, reported as `pass@1`, `pass@10`, and `pass@100` by default.

**Human URL:** [https://github.com/openai/human-eval](https://github.com/openai/human-eval)

#### Tags

Benchmark, Code Generation, Functional Correctness, Pass@k, Reference-Based

#### Properties

- [GitHubRepository](https://github.com/openai/human-eval)
- [Paper](https://arxiv.org/abs/2107.03374)
- [Dataset](https://huggingface.co/datasets/openai/openai_humaneval)

### GAIA Benchmark

GAIA is "a benchmark for General AI Assistants," published in 2023 (arXiv 2311.12983). It tests general-purpose AI agent capability across reasoning, tool use, multi-modality, and web browsing, with a public leaderboard hosted on Hugging Face for community submissions. The benchmark has become a reference point for evaluating agentic systems that combine an LLM with tools and a browser.

**Human URL:** [https://huggingface.co/gaia-benchmark](https://huggingface.co/gaia-benchmark)

#### Tags

Benchmark, AI Agents, Reasoning, Tool Use, Leaderboard

#### Properties

- [Dataset](https://huggingface.co/datasets/gaia-benchmark/GAIA)
- [Paper](https://arxiv.org/abs/2311.12983)
- [Leaderboard](https://huggingface.co/spaces/gaia-benchmark/leaderboard)

### AgentBench

AgentBench is the first benchmark designed to evaluate LLM-as-Agent across a diverse spectrum of environments. It bundles 8 environments — 5 newly created (Operating System, Database, Knowledge Graph, Digital Card Game, Lateral Thinking Puzzles) and 3 adapted (House-Holding from ALFWorld, Web Shopping from WebShop, Web Browsing from Mind2Web). The benchmark requires roughly 4,000 dev-set and 13,000 test-set interactions per model.

**Human URL:** [https://github.com/THUDM/AgentBench](https://github.com/THUDM/AgentBench)

#### Tags

Benchmark, AI Agents, Multi-Environment, LLM-as-Agent, Tsinghua

#### Properties

- [GitHubRepository](https://github.com/THUDM/AgentBench)
- [Paper](https://arxiv.org/abs/2308.03688)
- [Leaderboard](https://llmbench.ai/agent)

### BIG-Bench

The Beyond the Imitation Game Benchmark (BIG-Bench) is "a collaborative benchmark intended to probe large language models and extrapolate their future capabilities." It contains more than 200 tasks across JSON-based simplified tasks and programmatic tasks; a curated subset (BIG-Bench Lite) of 24 tasks is provided as the canonical headline measurement. Maintained on GitHub by Google with open community task submissions.

**Human URL:** [https://github.com/google/BIG-bench](https://github.com/google/BIG-bench)

#### Tags

Benchmark, Collaborative, Multitask, Google, BIG-Bench Lite

#### Properties

- [GitHubRepository](https://github.com/google/BIG-bench)
- [Paper](https://arxiv.org/abs/2206.04615)
- [Documentation](https://github.com/google/BIG-bench/blob/main/README.md)

## Common Properties

- [GitHubOrganization](https://github.com/api-evangelist)
- [JSONSchema - Eval Run Schema](https://raw.githubusercontent.com/api-evangelist/evals/refs/heads/main/json-schema/evals-eval-run-schema.json)
- [JSONSchema - Eval Suite Schema](https://raw.githubusercontent.com/api-evangelist/evals/refs/heads/main/json-schema/evals-eval-suite-schema.json)
- [JSONSchema - Eval Case Schema](https://raw.githubusercontent.com/api-evangelist/evals/refs/heads/main/json-schema/evals-eval-case-schema.json)
- [JSONSchema - Scorer Schema](https://raw.githubusercontent.com/api-evangelist/evals/refs/heads/main/json-schema/evals-scorer-schema.json)
- [JSONSchema - Judge Schema](https://raw.githubusercontent.com/api-evangelist/evals/refs/heads/main/json-schema/evals-judge-schema.json)
- [JSONSchema - Dataset Schema](https://raw.githubusercontent.com/api-evangelist/evals/refs/heads/main/json-schema/evals-dataset-schema.json)
- [JSONStructure - Eval Run Structure](https://raw.githubusercontent.com/api-evangelist/evals/refs/heads/main/json-structure/evals-eval-run-structure.json)
- [JSON-LD](https://raw.githubusercontent.com/api-evangelist/evals/refs/heads/main/json-ld/evals-context.jsonld)
- [Vocabulary](https://raw.githubusercontent.com/api-evangelist/evals/refs/heads/main/vocabulary/evals-vocabulary.yml)

## Features

| Name | Description |
|------|-------------|
| LLM-as-a-Judge Scoring | A second LLM evaluates the output of the system-under-test, producing a numeric or categorical score and (optionally) a written rationale. The dominant scoring mode for free-form text outputs across Braintrust, LangSmith, DeepEval, Weave, TruLens, Phoenix, and Patronus. |
| Reference-Based Scoring | Compares model output against a ground-truth expected answer using exact match, BLEU, ROUGE, embedding similarity, or task-specific equality (e.g. unit-test pass/fail). The native mode for benchmarks like MMLU, HumanEval, and GAIA. |
| Reference-Free Scoring | Assesses output quality without ground truth — toxicity, coherence, faithfulness against retrieved context, criterion adherence. Enables online (production-traffic) evaluation where labels do not exist. |
| Pairwise Comparison | A judge ranks two candidate outputs A vs B (or a tie). Useful when absolute scoring is hard but relative preference is reliable. Surfaced explicitly by LangSmith and used widely in chatbot arenas. |
| Benchmark-Aligned Evaluation | Runs the system-under-test against a standardized public dataset (MMLU, HumanEval, GAIA, AgentBench, BIG-Bench) to produce comparable, headline scores. The basis of model leaderboards. |
| Human-Rated Scoring | Domain experts or end users provide thumbs-up/down, Likert ratings, or written critiques. Used as ground truth, as a judge-calibration signal, and as a final acceptance gate before production. |
| RAG Triad | Three feedback functions — groundedness, context relevance, answer relevance — codified by TruLens and widely adopted across Ragas, Phoenix, DeepEval, and LangSmith for evaluating retrieval-augmented generation pipelines. |
| Agent and Tool-Use Evaluation | Evaluating multi-step agent trajectories: did the agent pick the right tool, did the tool call succeed, did the final answer satisfy the goal? Supported by Inspect AI, Galileo, Weave, LangSmith, Braintrust, and benchmarks like AgentBench and GAIA. |
| Online Production Monitoring | Eval scorers (typically reference-free LLM judges and Luna-style distilled evaluators) attach to live traffic via tracing/observability layers (Phoenix, Arize, Helicone, Galileo, Weave) to flag regressions in real time. |
| Red-Team / Safety Evaluation | Adversarial test suites probe jailbreaks, prompt injection, PII leakage, harmful content, and policy violations. First-class in Promptfoo, Patronus, Galileo, and Inspect AI's safety evals. |

## Use Cases

| Name | Description |
|------|-------------|
| Model Selection | Run candidate models (GPT-5, Claude 4.7, Gemini 3, open-weight) against a shared eval suite to choose the best fit for a specific application by quality, cost, and latency. |
| Prompt Engineering Iteration | Compare prompt variants in a matrix-style eval (Promptfoo, LangSmith experiments, Braintrust experiments) to pick the best prompt before shipping. |
| Regression Detection in CI/CD | Wire an eval suite into CI so a pull request that drops a key scorer below a threshold fails the build, preventing quality regressions from reaching production. |
| RAG Pipeline Tuning | Use RAG-triad scores (groundedness / context relevance / answer relevance) and faithfulness to tune chunking, embedding, reranking, and prompt choices. |
| Agent Trajectory Quality | Score multi-step agent runs on tool-selection correctness, step efficiency, and final-answer faithfulness — the core measurement for production agentic apps. |
| Hallucination and Safety Guardrails | Deploy dedicated judge models (Lynx, GLIDER, Luna) to flag hallucinations, toxic content, PII leakage, and policy violations in real time. |
| Frontier Capability and Safety Assessment | Independent labs (UK AISI, US AISI) run capability and safety evaluations on frontier models before release, using frameworks like Inspect AI. |
| Public Leaderboard Reporting | Submit a model's scores against MMLU, HumanEval, GAIA, AgentBench, and BIG-Bench to position it on community leaderboards and back marketing claims with reproducible numbers. |

## Integrations

| Name | Description |
|------|-------------|
| OpenTelemetry | Phoenix, TruLens, Weave, and most modern eval platforms ingest LLM traces via OpenTelemetry, making eval a layer on top of standard observability. |
| LangChain / LangGraph | LangSmith is the native eval tier for LangChain/LangGraph apps; most other platforms also integrate. |
| LlamaIndex | Ragas, DeepEval, and Phoenix integrate directly with LlamaIndex for RAG evaluation. |
| Hugging Face Datasets | MMLU, HumanEval, and GAIA are distributed as Hugging Face datasets and consumed by every eval framework. |
| CI/CD (GitHub Actions, etc.) | Braintrust, Promptfoo, LangSmith, and DeepEval ship CI integrations to fail builds on regression. |
| Snowflake | OpenAI Evals can log eval results to Snowflake; TruLens (Truera) is now part of Snowflake. |

## Repository Layout

```
evals/
├── apis.yml                         ← This index
├── README.md                        ← You are here
├── json-schema/                     ← JSON Schemas for eval entities
│   ├── evals-eval-run-schema.json
│   ├── evals-eval-suite-schema.json
│   ├── evals-eval-case-schema.json
│   ├── evals-scorer-schema.json
│   ├── evals-judge-schema.json
│   └── evals-dataset-schema.json
├── json-structure/                  ← JSON Structure counterparts
├── json-ld/
│   └── evals-context.jsonld         ← Linked-data context
├── vocabulary/
│   └── evals-vocabulary.yml         ← Operational + capability taxonomy
└── examples/                        ← Sample eval run records
    ├── evals-eval-run-rag-faithfulness-example.json
    ├── evals-eval-run-humaneval-example.json
    ├── evals-eval-run-pairwise-example.json
    ├── evals-eval-run-mmlu-example.json
    ├── evals-eval-suite-example.json
    ├── evals-eval-case-example.json
    ├── evals-judge-example.json
    ├── evals-scorer-example.json
    └── evals-dataset-example.json
```

## Maintainers

- **Kin Lane** — info@apievangelist.com
