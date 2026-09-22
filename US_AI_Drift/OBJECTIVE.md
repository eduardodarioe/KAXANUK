# Objective — US_AI_Drift

> **A second, self-contained hypothesis, step 1 of 8 for this idea.** Different market, different
> universe, different mechanism from the root `OBJECTIVE.md` — that one is untouched by anything
> here. Written before any earnings-surprise or return data was looked at: the only market data
> touched so far is price history length and average daily volume, used to build the universe.

## The objective, in one paragraph

**The claim:** among the 32 large-cap, NYSE- and Nasdaq-listed companies in
`Universe/Investable_Universe.csv`, a company that beats consensus quarterly revenue by more than
3% in a quarter reported from Q4 2022 onward continues to outperform an equal-weighted basket of
that same quarter's non-beating universe members over the following one to three months, net of
costs. **Its source of edge** is behavioral under-reaction — post-earnings-announcement drift,
PEAD, a documented anomaly (Bernard & Thomas, 1989) — claimed to be unusually strong in this
specific universe because a beat driven by AI-related revenue is a newer, harder-to-model line than
a mature segment, and sits inside a narrative that has swung between hype and skepticism since
generative AI became a distinct investment theme; a confirmed beat is under-trusted for longer than
an equivalent beat in an established business. **The other side** is whoever does not update on a
single earnings print: index and passive funds that rebalance on a schedule, not on a surprise;
active managers who have been burned by AI-narrative overhype before and discount even confirmed
beats on principle; and the crowd that already prices the obvious case instantly, which is why the
edge, if real, is more likely to survive in the less-watched names in this universe than in Nvidia,
already the most covered stock in the sample. **The test**, fixed now: for each qualifying quarter
since Q4 2022, open a position at the next available price after the earnings date, long the
beating name(s) and short an equal-weighted basket of that same quarter's non-beating universe
members, priced net of costs, and read the cumulative spread at 1, 2 and 3 months, then pass it
through attribution to see what survives market and, in particular, momentum exposure — PEAD and
momentum are known to overlap, and the 2026 macro reversal logged in `Bibliotheca/` is a live
reminder that a raw spread can come from beta, not from the earnings event. **The kill switch:** if
the spread is not positive net of costs across a clear majority of qualifying quarters, or if
attribution assigns it to momentum or another known factor instead of to the earnings-beat event
itself, the idea is abandoned and not re-tuned. The exact trial count — how many quarters actually
qualify — is unknown until step 3 pulls fundamentals data, and will be published in `FINDINGS_1`
before any result from this test is read as evidence, not after.

## The main idea

*Own the AI-exposed company whose earnings just confirmed the story, against the ones in the same
universe whose earnings that quarter did not, on the belief that a beat driven by an unfamiliar
revenue line is trusted more slowly than one from a familiar business.*

Both halves are plain-language features: **the signal** is a mechanical revenue-surprise threshold
(more than 3% above consensus), not a judgment call about whether a company's AI story is
convincing; **the sizing** is equal weight against the same quarter's non-beating universe members.
Neither is clever, and both can be explained in a sentence, which is what lets attribution later say
which half earned the return.

## The objective

A finished version answers one question honestly: **does the market under-react to AI-specific
earnings beats more than it under-reacts to ordinary ones, or is this just the well-known PEAD
anomaly wearing an AI label?** The deliverable is not a Sharpe. It is a rule simple enough that when
it works we can say why, and when it fails we can say which part failed.

The one design constraint: **radical simplicity.** One mechanical threshold, one universe, no
fitted parameters, no qualitative judgment about which beats "count" as AI-driven. Complexity, such
as weighting by beat size or restricting to beats where AI is named on the earnings call, is added
one lever at a time, and each addition must beat this baseline to earn its place.

## The universe

`Universe/Investable_Universe.csv`: **32 equities on NYSE and Nasdaq**, in US dollars, screened
through FMP for ten years of daily history and enormous liquidity — every member trades well over
USD 500 million a day on average, so unlike the Xetra universe, liquidity was never the binding
constraint here.

| Criterion (from the assignment) | How it is met |
| --- | --- |
| One asset class, one market | equities on NYSE and Nasdaq |
| 30 to 100 names | 32 |
| A liquidity floor | every member's average daily traded value exceeds USD 500 million; not a binding constraint |
| Ten years of daily history | every member has daily data from 2016-01-04 |
| Point-in-time | **not met, and cannot be fully met. See the limits below — this is the serious one.** |

**Limits, stated now and not discovered later:**

- **"AI-exposed" is not a point-in-time criterion, and this is the central weakness of the whole
  universe.** These 32 names were chosen because they are, *today*, widely described as AI-exposed.
  In 2016, when the price history starts, nobody could have written down a rule that produced this
  same list — "AI-exposed" was not yet a nameable investment theme. This is survivorship bias by
  construction: the universe is a hindsight-selected set of names that turned out to matter for AI,
  not a definable population as of any past date. **This is why the claim's test window starts at
  Q4 2022**, roughly when generative AI became a distinguishable, ex-ante-nameable theme in
  earnings calls and coverage, rather than reaching back to 2016. Even from Q4 2022, the underlying
  universe membership itself was still chosen with hindsight, and that gap does not close.
- **Excluded for a short history, not for illiquidity:** several of the most AI-native software
  and hardware names by revenue growth — `PLTR` (2020), `SNOW` (2020), `CRWD` (2019), `DDOG`
  (2019), `NET` (2019), `MDB` (2017), `APP` (2021), `ARM` (2023), `DELL` (relisted 2016-08) — do
  not have the full ten years and were left out rather than silently missing.
- **Two members are foreign-domiciled ADRs on a US exchange** (`TSM`, `ASML`), and a third (`SAP`)
  is a European company's US-listed line, distinct from its Xetra listing already in the other
  hypothesis's universe. Kept because the criterion is one *market*, not one country of
  incorporation — the same logic that would keep a Mexican ADR on the NYSE in a US universe.
- **`AAPL` has the least AI-specific revenue line in the universe** and is kept deliberately as an
  internal control case: if the drift shows up in `AAPL` as strongly as in the semiconductor and
  hyperscaler names, the "AI" part of the story is doing less work than claimed.

## The claims inside that sentence

They are tested separately and their status is not the same.

| | Claim | Status |
| --- | --- | --- |
| **1. The spread** | a universe member beating revenue by more than 3% outperforms that quarter's non-beaters over 1-3 months, net of costs | **untested** |
| **2. The mechanism** | the drift is larger in this AI-exposed universe than the roughly 18% annualized Bernard & Thomas (1989) found in a broad market, i.e. this is more than generic PEAD | **untested, and the harder claim to clear** |
| **3. The construction** | the equal-weighted non-beater basket removes exposure to the market and to the AI theme generally, isolating the beat event itself | **true by construction, untested as a source of return** |

## What is not claimed

- **Not that the parameters are right.** There are none to tune: the 3% surprise threshold, the
  universe and the 1/2/3-month windows are set here, before any return or earnings-surprise data is
  seen. That is a defence against data-snooping and not evidence of optimality.
- **Not that this is out of sample.** Nothing is until an experiment reaches step 7.
- **Not that this is statistically decisive.** The trial count is unknown until step 3 pulls
  fundamentals; whatever it turns out to be, it is a handful of years of one universe's quarters,
  not an independent-decade sample. It can reject the idea; it cannot make it certain.
- **Not that "AI-exposed" is a settled or defensible point-in-time category.** It is explicitly
  not — see the universe limits above. This is the single biggest weakness of this hypothesis, and
  it is why the test window is bounded to start at Q4 2022 rather than claimed over the full ten
  years of price history the universe happens to have.
- **Not that the premise is more than sourced.** Three dated notes are in `Bibliotheca/` —
  including one that argues against reading any 2026 spread at face value, because a macro reversal
  hit the two most AI-exposed names in the universe hard enough to swamp any earnings-driven signal
  in raw returns that year. See `Bibliotheca/BIBLIOGRAPHY.md`, Part 1.
- **Not that this can be sized without checking capacity.** All 32 names are highly liquid, so
  unlike the VW hypothesis this is not a borrow-cost or free-float problem — it is a crowding
  problem instead: if PEAD in mega-cap tech were easy money, well-funded quant desks would already
  be capturing it, which is itself a reason to expect a small or zero result here.
- **Trial count: two.** This is the second idea tried in this repository; the Volkswagen-relative
  hypothesis in the root `OBJECTIVE.md` was the first.

## The seven questions, answered

| # | Question | Answer |
| --- | --- | --- |
| 1 | Why does the edge exist? | a new, hard-to-model revenue line is under-trusted longer than a familiar one, on top of the general PEAD effect |
| 2 | Who is on the other side? | schedule-driven passive funds and managers discounting AI narratives after past hype cycles |
| 3 | Risk premium or mispricing? | a mispricing claim; PEAD's own literature (Bernard & Thomas, 1989) already rejects the risk-premium reading for the generic effect, and attribution checks whether that holds here too |
| 4 | How many independent bets a year? | unknown until step 3; bounded by 32 names times a handful of quarters since Q4 2022 — likely still few, and the honest answer is "count it before claiming it" |
| 5 | Does it survive costs, and how much can it hold? | to be measured net; capacity is not the binding constraint here, crowding is |
| 6 | When does it fail, and would I hold through it? | when a macro regime (like 2026's) dominates the cross-section, or when attribution shows the spread is just momentum wearing an earnings label |
| 7 | How many ideas before this one? | one — the Volkswagen-relative hypothesis at the repository root |

**Where this stands, with every number and its caveats:** not yet measured; nothing from this
folder has reached `RESULTS.md` yet.
How work is done here, and the bar a result has to clear: [`../AGENTS.md`](../AGENTS.md).
