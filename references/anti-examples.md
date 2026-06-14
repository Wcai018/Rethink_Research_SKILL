# Anti-Examples: Three Failure Patterns to Avoid

These are the most common ways a research direction looks valid but isn't.
Use this file when Stage 1–3 results feel uncertain, or when you want to
pressure-test your gap before committing to Stage 4–5.

---

## Pattern A: Fake Gap (Literature Already Solved It)

**Example direction:** "Use Transformers for multivariate time series prediction"

**Why it looked valid:** The researcher searched broadly and found that "Transformers + time series"
had few papers in 2020. The gap seemed real.

**What went wrong:** A deeper search at NeurIPS, ICLR, and ICML 2022–2024 reveals
Autoformer, PatchTST, iTransformer, TimesNet, and 50+ follow-up papers covering
exactly this direction. The gap was filled — the researcher's Stage 3 search was
too shallow or too early.

**How this framework catches it:** Stage 3 requires checking top venues for the last
2 years specifically. A gap that existed in 2021 may be completely saturated by 2024.

**Lesson:** Date your literature map. "No paper in 2020" ≠ "no paper in 2024."
Repeat Stage 3 searches within 3 months of submission.

---

## Pattern B: Engineering-Redundant Research

**Example direction:** "Build an LLM system that auto-generates SQL from natural language"

**Why it looked valid:** Relatively few academic papers formally studied Text-to-SQL with
LLMs as of early 2022. The academic gap seemed real.

**What went wrong:** GitHub Copilot, Microsoft Copilot for Azure SQL, and numerous
open-source Text2SQL tools (e.g., DAIL-SQL, SQLCoder) already achieve >90% accuracy
on standard benchmarks (Spider, BIRD) for common query patterns. The engineering
community solved this before academia published a formal treatment.

**How this framework catches it:** Stage 3.5 (Reality Solution Map) forces you to check
open-source systems and industrial tools before finalizing the gap. If engineering
coverage is >80%, the research gap shifts from "can we do this?" to "why does it fail
on edge cases / adversarial inputs / cost constraints?"

**Lesson:** The real gap after engineering covers 80% is usually about robustness,
interpretability, cost, or formal guarantees — not raw capability.

---

## Pattern C: Over-Abstract (Unfalsifiable Framing)

**Example direction:** "Construct a universal cross-domain knowledge transfer framework
for heterogeneous AI systems"

**Why it looked valid:** Knowledge transfer and domain adaptation are well-studied,
high-impact topics. The "universal" framing sounds ambitious and impactful.

**What went wrong:** "Universal" and "cross-domain" without concrete constraint E in
the Stage 4 reframing means there is no specific benchmark that can validate or
falsify the claim. Reviewers will ask: universal across what domains exactly?
Heterogeneous in what sense? The paper cannot be evaluated.

**How this framework catches it:** Stage 4 validation checklist item: "Is constraint E
specific enough to enable a benchmark?" An unfalsifiable direction fails this check.
Stage 5 P0 identification also fails — there is no single mechanism whose failure
collapses the paper, because the framing is too broad to have a core.

**Lesson:** Every constraint E must map to at least one existing or constructible
benchmark. If you cannot name it, narrow the framing until you can.

---

## When to Consult This File

- After Stage 1, if your gap verification passes fewer than 2 checks
- After Stage 3, if literature coverage feels thin but you're unsure why
- After Stage 3.5, if you find engineering coverage >60%
- After Stage 5, if you cannot identify a clear P0

If your direction matches Pattern A, B, or C: do not proceed to writing.
Return to Stage 1 and recompress the field with the new information.
