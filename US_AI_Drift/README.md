# US_AI_Drift — a second, self-contained hypothesis

This folder is a second investment hypothesis, kept separate from the repository's root files so
that neither hypothesis overwrites or gets confused with the other.

| | This folder | The repository root |
| --- | --- | --- |
| Market | NYSE / Nasdaq (US) | Xetra (Germany) |
| Idea | Large-cap AI-exposed names drift up after a big earnings beat | Volkswagen underperforms its German auto peers |
| Direction | Long only | Long/short pair |
| Source of edge | Behavioral — post-earnings-announcement drift | Behavioral — under-reaction to disclosed information |

It mirrors the root's own layout so the same conventions apply without having to relearn them:

```
US_AI_Drift/
├── README.md                  this file
├── OBJECTIVE.md                the hypothesis: claim, edge, other side, test, kill switch
├── Universe/
│   └── Investable_Universe.csv the seed: 32 US-listed AI-exposed equities
└── Bibliotheca/
    ├── BIBLIOGRAPHY.md         the index for this hypothesis's own sources
    ├── Papers/                 one note per source
    └── Books/
```

**Why two hypotheses in one repository, rather than a second repository.** The KaxaNuk template is
built around one strategy per repository — `AGENTS.md` at the root says so. This folder is a
deliberate, practical exception for a course context where exploring a second idea alongside the
first is worth more than strict adherence to that convention: nothing here writes to, reads from,
or depends on the root's `OBJECTIVE.md`, `Universe/`, or `Bibliotheca/`, so the two stay genuinely
independent. If this idea is ever taken further than a course exercise, it earns its own repository
at that point, the way the template intends.

Shared, not duplicated: the reading list behind the research process itself — survivorship bias,
look-ahead, overfitting, costs, dirty data — lives once, in the root `Bibliotheca/BIBLIOGRAPHY.md`,
Part 5, and this folder's own index points there instead of repeating it.
