---
name: rethink-research
description: >
  A structured framework for transforming vague research ideas into publication-ready directions.
  Use this skill whenever a user mentions: finding a research gap, developing a research idea,
  validating novelty, writing a related work section, identifying contributions, scoping a paper,
  or asking "is this idea good enough to publish". Also trigger when users say things like
  "I want to work on X, is there a gap?", "help me think through my research direction",
  "what's missing in the literature on X", or "how do I frame my contribution". This skill
  enforces three grounding layers — academic literature, engineering reality, and structural gap
  reasoning — to kill bad ideas fast and sharpen good ones.
---

# Rethink Research Skill

A filter framework for transforming vague research ideas into grounded, publication-ready directions.

> ⚠️ This is a **filter**, not a generator. Its primary value is **killing bad ideas fast**.
> Used rigidly on very nascent directions, it may over-filter. See `references/anti-examples.md`.

---

## Quick Start

Input your idea in any form — a topic, a system concept, a vague direction:
- "LLM for debugging"
- "remote sensing mangrove modeling"
- "efficient transformer for time series"

Then work through Stages 0 → 5 in order. **Do Stage 3.5 before or in parallel with Stage 3.**

---

## Stage 0: Problem Input

Capture the raw idea. No filtering yet. Write it down exactly as it comes.

**Output template:**
```
Raw idea: _______________
Domain: _______________
Motivation (why now?): _______________
```

---

## Stage 1: Field Compression

Summarize the field in 3 parts, then produce one compressed statement.

- What is progressing **fast**?
- What is still **weak**?
- What is the **structural gap** between them?

**Compressed statement format:**
> "X is advancing quickly, Y is improving moderately, but the interaction between X and Y remains weak."

### Verifying the gap is real (not just perceived)

Run ≥2 of these checks. If <2 confirm weakness, dig deeper before proceeding.

| Check | Method | Threshold for "weak" |
|-------|--------|----------------------|
| Literature co-occurrence | Search top venues for X+Y co-occurrence in titles/abstracts, last 2 years | <5% of papers in either field mention both |
| Pipeline independence | Are X and Y maintained by separate teams in industry, with hand-off interfaces? | Yes = weak interaction |
| Benchmark absence | Is there a standard benchmark measuring X→Y or Y→X joint performance? | No = weak interaction |
| Citation graph gap | Do the most-cited papers in X cite the most-cited papers in Y? | No = weak interaction |

**Top venues by domain** → see `references/venues.md`

**Output template:**
```
Fast progress: _______________
Slow / weak: _______________
Structural gap: _______________

Compressed statement: "_______________"

Gap verification:
- [ ] Literature co-occurrence < 5%: Y/N
- [ ] Pipeline independence: Y/N
- [ ] No joint benchmark: Y/N
- [ ] Citation graph gap: Y/N
Checks passed: ___ / 4  →  Gap structurally real? Y/N
```

**Example (LLM debugging):**
```
Fast progress: LLM code generation (CodeLlama, GPT-4o)
Slow / weak: Automated debugging and fault localization
Structural gap: Generation and debugging are not jointly modeled

Compressed statement: "LLM code generation is advancing rapidly, static analysis
tools are improving, but joint modeling of generation and debugging is nearly
absent from top-venue work."

Gap verification:
- [x] Literature co-occurrence < 5%: Y
- [x] Pipeline independence: Y
- [x] No joint benchmark: Y
- [ ] Citation graph gap: unclear
Checks passed: 3 / 4  →  Gap structurally real? Y
```

---

## Stage 2: Task / System Decomposition

Break the problem into a full pipeline. Identify where the real bottleneck is.

**Default pipeline template (adapt as needed):**

| Step | Typical Content | TCS/Theory Adaptation | Systems Adaptation |
|------|----------------|----------------------|-------------------|
| Input | Raw data / problem instance | Problem specification | Workload trace |
| Preprocessing | Cleaning, normalization | Instance reduction / symmetry breaking | Profiling / instrumentation |
| Representation | Feature extraction, embedding | Mathematical formalization | Design space definition |
| Modeling | Architecture, loss, objective | Algorithm / proof structure | Trade-off model |
| Inference / Execution | Decoding, search | Complexity-critical subroutine | Runtime execution |
| Evaluation | Metrics, baselines | Proof of correctness / competitive ratio | Latency, throughput, cost |
| Deployment | Latency, maintainability | Generality of assumptions | Operational constraints |

For each step, answer:
- What is the bottleneck here?
- What is done manually / by heuristic?
- Where are AI or formal methods already strong?

**Key question:** *What part of the pipeline is actually the bottleneck?*

---

## Stage 3.5: Reality Solution Map ← Do This Before Stage 3

> ⚠️ Do Stage 3.5 **before** Stage 3. Engineering reality should anchor your gap definition,
> not the other way around. If engineering already solves 80% of the problem, your research
> gap is fundamentally different from what papers suggest.

### 3.5.1 Industrial / Engineering Solutions
- How do practitioners actually solve this today?
- What toolchains, heuristics, pipelines exist in production?

### 3.5.2 Open-Source Systems
- Relevant GitHub tools, production frameworks, agent systems

### 3.5.3 Human Expert Baseline
- How do domain experts solve this manually?
- What are their rules of thumb and decision heuristics?

**Output template:**
```
Industrial solution: _______________
Coverage estimate: ~___% of problem solved
Key limitation: _______________

Open-source tools: _______________
Human expert baseline: _______________

Conclusion: Engineering solves [X]% → research gap is about [remaining Y%]
```

---

## Stage 3: Top-Tier Literature Map

Map related work into 3 layers. **A valid research gap must NOT already be solved in SOTA papers.**

For venue selection by domain, see → `references/venues.md`

### 3.1 SOTA Systems
- Best-performing models / systems
- Benchmark leaders
- Foundation models in the field

### 3.2 Mechanism Papers
- Key architectural innovations
- Learning paradigms / proof techniques
- Optimization strategies

### 3.3 Failure Analysis Papers
- Known weaknesses of SOTA
- Generalization failures, dataset biases, evaluation limitations

**Output template:**
```
SOTA systems: _______________
Key mechanism papers: _______________
Known failure modes: _______________

Gap confirmed not in literature? Y/N
Gap confirmed not solved in engineering (from 3.5)? Y/N
```

---

## Stage 4: Research Problem Reframing

Reformulate your problem using the template for your research type:

**ML / AI:**
> "Given **A** input, learn **B** representation, enabling **C** mechanism, to produce **D** output under constraint **E**."

**Systems / Engineering:**
> "Given **A** workload/environment, design **B** architecture/protocol, exploiting **C** trade-off, to achieve **D** performance guarantee under constraint **E**."

**Theory / Algorithm:**
> "Given **A** problem class with property **B**, construct **C** algorithm/proof, achieving **D** complexity/correctness bound, under assumption **E**."

### Validation checklist:
- [ ] Is it feasible with current tools and data?
- [ ] Is it already solved in top-venue literature?
- [ ] Is it already solved in engineering practice?
- [ ] Is it still scientifically meaningful if engineering partially covers it?
- [ ] Is constraint **E** specific enough to enable a benchmark?

If any box is unchecked → revise the framing before continuing.

---

## Stage 5: Innovation Decomposition

Break the system into components and identify what is genuinely missing.

**Components to analyze:**
- Representation
- Modeling / Algorithm
- Constraints
- Optimization / Proof strategy
- Feedback loop / Evaluation protocol

For each component:
1. What do existing papers do?
2. What do engineering systems do?
3. What is still missing?

Each claimed innovation must satisfy:
- ✔ Grounded in literature (Stage 3 confirms gap)
- ✔ Not trivially solved in engineering (Stage 3.5 confirms gap)
- ✔ Experimentally or formally testable

### Priority classification

| Priority | Label | Criteria | Strategy |
|----------|-------|----------|----------|
| P0 | Core Innovation | If this fails, the paper collapses; no existing paper solves this | Must do. Allocate 60%+ effort. |
| P1 | Supporting Innovation | Strengthens the core; partially solved or heuristic in existing work | Do if time permits. Can be simplified. |
| P2 | Systematic Innovation | Makes the pipeline work; engineering-heavy, lower novelty risk | Do minimally. Often "implementation details." |

### Decision Tree: If you can only choose one innovation

**Q1:** Does your system have a core assumption — if wrong, the whole paper collapses?
→ Yes → that assumption's corresponding mechanism = **P0**
→ No → continue

**Q2:** Which component is completely absent from engineering solutions (not just done poorly — absent)?
→ Found one → that component = **P0**
→ None → your work may be a P1 cluster; return to Stage 3.5 and re-examine

**Q3:** Which innovation, if removed, makes your system indistinguishable from existing baselines?
→ That one = **P0**; everything else drops to P1/P2

**Fallback:** If all three questions yield no clear answer → return to Stage 1. The direction is not yet mature enough to decompose.

---

## Output: Final Research Summary

```
Research direction: _______________
Research type: [ ] ML/AI  [ ] Systems  [ ] Theory/Algorithm  [ ] Other

Problem reframing:
"Given ___, [learn/design/construct] ___, enabling/exploiting ___, to produce/achieve ___
under constraint ___."

Gap evidence:
- Literature gap confirmed: Y/N  (venues checked: ___)
- Engineering gap confirmed: Y/N  (tools checked: ___)

Innovation points:
- P0: _______________
- P1 (optional): _______________
- P2 (optional): _______________

Estimated feasibility: High / Medium / Low
Reason to proceed / kill: _______________
```

---

## Reference Files

- `references/venues.md` — Top venues by domain (CV, NLP, Systems, Theory, etc.)
- `references/anti-examples.md` — Three failure patterns to avoid (fake gap, engineering-redundant, over-abstract)
