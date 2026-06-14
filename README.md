# Rethink Research SKILL

> Kill bad research ideas fast. A Claude skill that filters research directions through literature, engineering reality, and structural gap analysis — before you waste months on a dead end.

## Install in Claude Code (One-Click)

Run these two commands in Claude Code terminal:

```bash
/plugin marketplace add Wcai018/Rethink_Research_SKILL
/plugin install rethink-research@rethink-research-marketplace
```

Start a new conversation. The skill auto-triggers when you say things like:
- *"Is there a research gap in X?"*
- *"Help me validate my research direction"*
- *"What's missing in the literature on X?"*
- *"How do I frame my contribution?"*

---

## What This Skill Does

Most research directions fail for one of three reasons:

1. The gap is already filled in literature (you didn't search deeply enough)
2. Engineering already solved it (you didn't check production tools)
3. The framing is too abstract to be falsifiable (you can't build a benchmark)

This skill is a **filter**, not a generator. It kills bad ideas fast so you can invest your effort only in directions that are genuinely novel, practically meaningful, and experimentally testable.

---

## The Five Stages

| Stage | Purpose |
|-------|---------|
| 0 | Capture raw idea |
| 1 | Compress the field, verify gap is structurally real |
| 3.5 | Reality check — what engineering already solves (**do this before Stage 3**) |
| 3 | Literature map — SOTA, mechanisms, failure analysis |
| 4 | Reframe the problem precisely (ML / Systems / Theory templates) |
| 5 | Decompose innovations into P0/P1/P2, identify your core |

---

## Structure

```
Rethink_Research_SKILL/
├── SKILL.md                    # Main framework (Stages 0–5)
├── marketplace.json            # Claude Code plugin registry
└── references/
    ├── venues.md               # Top venues by domain (CV, NLP, Systems, Theory…)
    └── anti-examples.md        # Three failure patterns with real examples
```

---

## License

MIT — Original framework design by [@Wcai018](https://github.com/Wcai018).
