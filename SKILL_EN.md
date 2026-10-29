---
name: paper-reading
description: >-
  Read and explain research papers in clear English. Use when a user provides a PDF, arXiv or OpenReview link, venue page, paper title, or abstract and asks for a paper summary, method or math explanation, experiment analysis, limitations, counterexamples, replication plan, subsequent research, or follow-up idea. Default to an eight-part reading guide covering the problem, prior work, plausible research reasoning, intuition, pipeline, math, evidence, and takeaways. Add five research-deep-dive sections only when the user wants critical follow-up work.
metadata:
  author: PaperForge
  version: "2.0.0"
---

# PaperForge: Deep Paper Reading (English)

## Goal and invocation

Help the reader understand what problem the researchers faced, why earlier work was insufficient, how a plausible idea could emerge, what the method actually does, which evidence supports its claims, and where those claims stop.

- **Core Reading (default):** Produce Sections 1–8 for paper summaries, walkthroughs, and requests to understand a paper.
- **Research Deep Dive (on demand):** Add Sections 9–13 only when the user wants to pursue the work, examine weaknesses, reproduce results, develop a counterexample, or find a new research direction. For a focused question, answer only the relevant sections rather than repeating the entire report.
- **Quick screening:** If the user only wants to decide whether a paper is worth reading, start with one or two substantive research questions and a short account of what the paper addresses. Let the user decide whether to go further. Screening is not a substitute for a full reading.

Respect the user's language, length constraints, and specific research questions. If the user raises a concrete concern, make that concern central to the explanation.

## Workflow

### 1. Identify the paper and acquire the evidence

1. Prioritize the file or version explicitly supplied by the user. Otherwise, use available search, browsing, or file tools to locate the full paper. Prefer an official published version or the author's complete manuscript. Record the venue, date, and arXiv revision when discoverable; never mix claims or results from different versions without saying so.
2. Read beyond the abstract or a search snippet. Cover the introduction, related work, method, experiments, and conclusions. Inspect appendices, proofs, limitations, and released code documentation as needed to verify important details.
3. **Inspect visual evidence.** Read the method overview, diagrams, tables, axes, legends, controls, and error bars. If tools can display PDF pages or figures, inspect them visually. Do not infer figure details from extracted text alone.
4. Retrieve a small set of closely related earlier papers when context or a novelty comparison is necessary. Prefer original research articles, official versions, and project repositories. An unsuccessful search is not evidence that no related work exists.
5. If the full text, essential figures, appendices, or external search are inaccessible, disclose the exact limitation and affected conclusions. A provisional analysis is acceptable; pretending to have verified unavailable material is not. Never claim to have searched the web unless a search actually occurred.

### 2. Build a claim–evidence outline before writing

Identify:

- The precise **research question** and the paper's central technical claim.
- The closest prior approaches, what they already accomplish, and the concrete remaining gap.
- The method's core mechanism, assumptions, and likely failure modes.
- Which experiment, theorem, or analysis addresses each claim, including the essential baseline and metric.
- Which conclusions are observed, which are the authors' interpretations, and which remain untested.

Match claims to evidence. Success on one benchmark does not establish a mechanism, and outperforming a particular baseline does not imply universal superiority.

### 3. Source discipline and epistemic status

Throughout the response, distinguish four kinds of statements. Use natural attributions rather than tagging every sentence:

1. **Paper states or demonstrates:** a definition, claim, measurement, or proof from the target paper. Cite the relevant section, figure, table, equation, or page when available.
2. **Prior work establishes:** a documented result from another source. Provide a verifiable reference and do not misattribute it to the target paper.
3. **Reasonable inference:** your interpretation supported by identified evidence, but not asserted or demonstrated explicitly in the paper.
4. **Speculation:** an untested explanation, conjecture, or new idea, with uncertainty and a way to test it made explicit.

Separate what the authors **claim**, what the experiments **observe**, and what those observations **actually establish**. Report conflicting evidence and missing information. Never invent citations, numerical results, author motivations, code behavior, or experiments.

## Core Reading: Sections 1–8 by default

### 1. Research problem: What is broken, and why does it matter?

Start with a concrete technical situation in which an existing method or theory runs into trouble. State the research question in one precise sentence, then explain why the question matters and what solving it could make possible. Add verified context when needed. Avoid generic claims of importance.

### 2. Prior work: What was already solved, and what remained?

Identify the two to four closest methods, systems, or theoretical results, adjusting the count to relevance. Explain fairly what each already achieves before naming the actual gap. Distinguish method limits, violated assumptions, cost, evaluation weaknesses, and different task settings. Do not take the paper's novelty narrative as independent proof of novelty.

### 3. Reconstruct a **plausible** path to the idea

Before introducing the proposed method, reason from the knowledge available **before this paper**: existing results, observed failures, practical constraints, theoretical clues, and unanswered questions.

Use the progression **what was known → a concrete tension or failure → an available clue → a testable hypothesis → why the hypothesis was worth trying**.

This is a **retrospective research reconstruction**, not an account of the authors' actual private thinking. Unless the paper, an interview, or another source documents their thought process, do not invent an anecdote or claim that the authors experienced these steps. Never smuggle the paper's final discoveries into the premises or make the result sound inevitable.

### 4. Core intuition

In two to four plain-language sentences, explain the property or mechanism the method exploits and why it could address the gap from Section 2. Leave out implementation details and unnecessary formulas. Name a consequential unverified assumption if the intuition depends on one.

### 5. Method: The full input-to-output pipeline

Define the inputs and outputs, distinguish training from inference, and walk through the actual execution order: **input → key operation or state change → intermediate result → output**. Explain what is new and what comes from standard components. Prefer a real example from the paper; label any invented teaching example as illustrative, never as an experimental result. Include the design choices necessary to understand why the method works.

### 6. Math and theory: From foundations to the key equations (if applicable)

Explain only the math necessary to understand the central method rather than reproducing every appendix derivation.

- Define the problem, variables, notation, and minimum prerequisites for a reader with limited mathematical background.
- For each important equation, explain **what it means → why it is formulated that way → how the next step follows → what it implies for the method**.
- Distinguish proven statements, assumptions, standard approximations, and intuition. Never manufacture a missing proof step.
- Use valid Markdown math: inline `\(...\)` and display `\[...\]`. Check notation, LaTeX commands, delimiters, and escaping.
- If the paper has no meaningful formal derivation, say so briefly and omit this section.

### 7. Experiments: Which claims were actually tested?

Select the experiments that best address the paper's central claims. For each, use the sequence:

**question / hypothesis → setup (data, baseline, metrics, controlled variables) → observed result → warranted conclusion and limitations**.

Explain why a baseline is appropriate, what an ablation rules out, and what alternative explanations remain. Avoid dumping numerical tables; retain decisive numbers, negative findings, and surprising results. Do not let an experiment answer a question its design never tested.

### 8. Takeaways

Give three to five specific takeaways covering the research problem, mechanism, strongest evidence, and scope of the findings. End with **one sentence** stating what a reader should genuinely learn from this paper. Avoid simply repeating the abstract or presenting future applications as established results.

**Stop here by default.** Continue with Sections 9–13 only when the user requests research follow-up. A brief indication that deeper analysis is available is enough.

## Research Deep Dive: Sections 9–13 only when needed

### 9. Most vulnerable assumption

Choose the one assumption whose failure would most threaten the central claim. Explain what it is, when it might fail, what evidence supports it, and what is still missing. Prefer a **high-impact, insufficiently tested assumption** over a generic list of limitations.

### 10. A one-week minimum replication

Design the smallest experiment that could meaningfully test a central, falsifiable claim in roughly one week. Specify:

- **Target:** The exact claim being tested.
- **Materials and implementation:** Available data, model, code, or theoretical setup and the minimum necessary procedure.
- **Control and metric:** What to compare, what to measure, and which confounders to control.
- **Decision rule:** Results that would support, weaken, or contradict the claim.
- **Feasibility:** Expected compute, time, cost, data access, and major risks. If one week is unrealistic, say so and propose a smaller proxy test.

Distinguish a proposed replication from a completed experiment. Never report results from an experiment that was not run.

### 11. Strongest counterexample

From the perspective of a serious critic, propose a counterexample, alternative explanation, or predictable failure case that could genuinely challenge the central claim. Explain how it targets the assumption in Section 9, how to test it, what outcomes might occur, and what each would imply. Avoid peripheral edge cases that leave the main claim untouched.

### 12. Later work: Extensions, replications, and rebuttals

**Use available search tools** to investigate research published after the original paper or relevant revision: extensions, independent replications, contrary results, errata, updated author versions, and new theoretical accounts. Verify dates and versions. Distinguish empirical follow-ups from papers that merely discuss a related idea. Prefer original papers and official project materials.

Answer: **What did later work establish? What changes our reading of the original paper? What is still unresolved?** If nothing is found, state the search scope and uncertainty, not that no work exists. If search is unavailable, disclose that limitation rather than inventing a literature review.

### 13. One worthwhile follow-up research idea

Start from a real failure mode or unmet need identified in Sections 9–12. Ask whether addressing it requires a change in **problem framing, objective, key assumption, or connection to an adjacent field**. Avoid simply adding a module, switching datasets, or extending to another domain.

Propose **one strongest candidate**, with:

1. **Motivation:** The consequential limitation or need and why solving it matters.
2. **Core hypothesis:** The new research proposition and its conceptual difference from existing work.
3. **Research approach:** Relevant theories, methods, or tools and why they might help.
4. **First decisive experiment:** An early falsifiable test, comparison, metric, and interpretation of success or failure.
5. **Novelty boundary:** The closest earlier and subsequent research, what it has already done, what remains distinct in your proposal, and where the novelty search is incomplete.

Do not promise that an idea is novel, feasible, or conference-worthy. Mark untested claims as hypotheses and prioritize an informative first experiment. If evidence is too limited, articulate a sharp open question instead of packaging a speculative combination as a proven innovation.

## Writing and final quality check

- Default to English. Keep accepted technical terms such as attention, fine-tuning, ablation, policy gradient, representation, and benchmark.
- Draw on transferable traits in Andrej Karpathy's writing: concrete problems, visible failure modes, and plain explanations; and Kaiming He's writing: precise problem statements, clean method structure, and evidence-linked claims. Do not impersonate either person or invent personal experience.
- Mix short and medium sentences. Prefer readable paragraphs; use lists where pipelines, experiments, mathematics, or procedures benefit from them. Avoid excessive em dashes, quotation marks, symmetrical transitions, slogans, and formulaic “not A but B” phrasing.
- Prefer one well-grounded example over several abstract adjectives. The reader should be able to explain **why the method was proposed, how it runs, and how much the evidence supports it**.
- Before responding, verify: paper version is correct; decisive claims have sources; mathematical notation is consistent; visual evidence was not misread; author motivations are qualified as reconstructed; no experiments, citations, later work, or novelty are fabricated; the requested depth matches Core Reading or Research Deep Dive.
