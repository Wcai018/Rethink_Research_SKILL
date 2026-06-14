# Rethink Research SKILL

A structured framework for transforming vague research ideas into grounded,
publication-ready directions — enforcing three layers of reality checking before
you commit to a direction.

## What This Skill Does

Most research directions fail for one of three reasons:

1. The gap is already filled in literature (you didn't search deeply enough)
2. Engineering already solved it (you didn't check production tools)
3. The framing is too abstract to be falsifiable (you can't build a benchmark)

This skill is a **filter**, not a generator. It kills bad ideas fast so you can
invest your effort only in directions that are genuinely novel, practically meaningful,
and experimentally testable.

## Structure

```
Rethink_Research_SKILL/
├── SKILL.md                    # Main framework (Stages 0–5)
└── references/
    ├── venues.md               # Top venues by research domain
    └── anti-examples.md        # Three failure patterns with real examples
```

## The Six Stages

| Stage | Purpose |
|-------|---------|
| 0 | Capture raw idea |
| 1 | Compress the field, verify gap is structurally real |
| 3.5 | Reality check — what engineering already solves (do BEFORE Stage 3) |
| 3 | Literature map — SOTA, mechanisms, failure analysis |
| 4 | Reframe the problem precisely (ML / Systems / Theory templates) |
| 5 | Decompose innovations into P0/P1/P2, identify your core |

## Key Design Decisions

- **Stage 3.5 before Stage 3**: Engineering reality anchors the gap before literature
  defines it — prevents being captured by paper-centric framing.
- **Three reframing templates**: ML/AI, Systems/Engineering, Theory/Algorithm —
  avoids the ML-centric bias of most research frameworks.
- **P0/P1/P2 classification with Decision Tree**: Forces explicit identification of
  the one innovation that, if it fails, collapses the whole paper.
- **Anti-examples grounded in real directions**: Pattern A (literature already solved),
  Pattern B (engineering-redundant), Pattern C (unfalsifiable framing).

## Usage

This skill is designed for use with Claude's skill system. Place the folder in your
skills directory and it will trigger when you discuss research directions, gap analysis,
novelty validation, or contribution framing.

You can also use SKILL.md directly as a standalone research thinking guide.

## License

MIT License. Original framework design by the repository author.
All venue lists, structural templates, and anti-example patterns are original work.
