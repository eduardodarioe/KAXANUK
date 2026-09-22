# Objective

> **Step 1 of 8, with `Bibliotheca/`.** One idea, one objective, and the claims inside it with
> their status. Written before any return was looked at: the only market data touched so far is
> average daily volume, used to set the liquidity floor of the universe.

## The objective, in one paragraph

**The claim:** Volkswagen preferred shares (`VOW3.DE`) earn less than an equal-weighted basket of
the other liquid Xetra automakers (`BMW.DE`, `MBG.DE`, `CON.DE`) over holding periods of three to
twelve months, net of costs. **Its source of edge** is behavioral under-reaction to disclosed
information, and specifically **not** a permanent control-discount: three dated events — the July
2025 operating-margin guidance cut, the loss of VW's China sales lead to BYD, and the Puebla shift
cut — put the deterioration in front of the market, and the claim is that each one is followed by
continued drift rather than an immediate, complete re-rating. This is a different claim from "VW
trades cheap because Lower Saxony and the Porsche and Piëch families hold it for control": that
older story predicts the same discount in every year, tariffs or not, and would need no China or
Mexico narrative at all — it is named here only to rule it out, not to lean on it. The door is open
only if the price keeps drifting in the weeks after each disclosure instead of jumping to its new
level immediately, which is what the test has to measure and not assume. **The other side** is the
holder who is not trading on return: the Lower Saxony state and the Porsche and Piech families
hold the voting control for reasons of control, index and cap-weighted funds hold VW by market
value and do not rebalance on margin trend, and short sellers face a thin free float, the squeeze
history of 2008 and borrow cost. **The test**, fixed now: an event study, not a rolling short —
a rolling position tests a permanent discount, and that is the mechanism just ruled out. Two of the
three dated disclosures already logged in `Bibliotheca/` are genuine single-day corporate
announcements: the 24 July 2025 operating-margin guidance cut and the 31 August 2026 Puebla shift
cut. At the next available price after each one, open a book short `VOW3.DE` and long an
equal-weighted basket of `BMW.DE`, `MBG.DE` and `CON.DE`, priced net of commission and a stated
borrow cost, and read its cumulative spread at 3, 6 and 12 months after the disclosure — continued
drift supports under-reaction, a jump that holds flat does not. The third source, the China
sales-lead loss to BYD, has no single disclosure date — it is a trend the market watched build
through 2023 and the January 2024 report only confirmed — so it is read differently: the same
spread, cumulated over the twelve months before that report against the twelve months after, asks
whether the drift was already priced in by the time the report caught up to it. All three readings
are passed through attribution to see what survives market and factor exposure.
**The kill switch:** this is a three-case study, not a three-sub-period statistical test, and it is
named as one — three events is too few to call a pass proof of anything. It is abandoned if the
spread does not keep drifting net of costs after **both** of the two clean disclosure events, since
with only two, a majority vote is not a meaningful bar. It is abandoned on the same result if
attribution assigns the drift to market beta or to a known factor instead of to VW itself. A pass
justifies widening the test to more automakers' disclosures before anything is sized up, not
increasing the position on these three cases alone.

## The main idea

*Own less of the automaker whose earnings are being eroded slowly, against the automakers that face
the same demand cycle without the same erosion.*

Both halves are plain-language features: **the signal** is the name itself, `VOW3.DE`, chosen by a
stated economic reason and not by a screen; **the sizing** is equal weight against a fixed peer
basket. Neither is clever, and both can be explained in a sentence, which is what lets attribution
later say which half earned the return.

## The objective

A finished version lets the desk answer one question honestly: **is a relative short on
Volkswagen a mispricing or only a bet on Germany's car cycle?** The deliverable is not a Sharpe. It
is a rule simple enough that when it works we can say why, and when it fails we can say which part
failed.

The one design constraint: **radical simplicity.** One name against three peers, no fitted
parameters. Complexity, such as generalising the rule to other automakers' own disclosure events,
is added one lever at a time, and each addition must beat this baseline to earn its place.

## The universe

`Universe/Investable_Universe.csv`: **42 equities on Xetra**, in euros, 13 sectors, with the
automakers as the group that matters and 37 other names for breadth.

| Criterion (from the assignment) | How it is met |
| --- | --- |
| One asset class, one market | equities on Xetra, all `.DE` |
| 30 to 100 names | 42 |
| A liquidity floor | average daily traded value of at least 20 million euros over the last 252 days |
| Ten years of daily history | every member has daily data from 2016-01-04 |
| Point-in-time | **not yet met. See the limits below.** |

**Limits, stated now and not discovered later:**

- **The floor was applied today, not as of each date.** A name that was liquid in 2016 and is not
  now is missing. That is survivorship bias and it is the first thing step 2 must fix by applying
  the floor per date.
- **Delisted names are mostly absent.** Wirecard returns no data from the provider at all, and
  Deutsche Wohnen and Covestro persist only as thinly traded remnants. The missing returns are
  disproportionately the bad ones, so any long side looks better than it was.
- **Excluded for a short history, not for illiquidity:** Porsche AG (listed 2022), Siemens Energy
  (2020), Siemens Healthineers (2018), Delivery Hero (2017).
- **`PAH3.DE` is Porsche SE**, whose value is mostly its Volkswagen stake. It stays in the universe
  but is not in the peer basket, because it moves with the thing being shorted.
- **The VW ordinary share `VOW.DE` is excluded** because it trades about 79 thousand shares a day
  against about 1.2 million for the preferred.

## The claims inside that sentence

They are tested separately and their status is not the same.

| | Claim | Status |
| --- | --- | --- |
| **1. The spread** | VOW3 earns less than the peer basket over three to twelve months, net of costs | **untested** |
| **2. The mechanism** | the price keeps drifting for months after each of the three disclosures, instead of re-rating in one jump | **untested** |
| **3. The construction** | equal weight against a fixed basket removes exposure to the market and to Germany's cycle | **true by construction, untested as a source of return** |

## What is not claimed

- **Not that the parameters are right.** There are none to tune: the peer set, the two clean
  disclosure events and the 3/6/12-month windows are set here, before any return is seen. That is a
  defence against data-snooping and not evidence of optimality.
- **Not that this is out of sample.** Nothing is until an experiment reaches step 7.
- **Not that this is statistically decisive.** Two clean disclosure events and one trend
  confirmation is three cases, not three independent draws — the kill switch already says so. It
  can reject the idea; it cannot make it certain.
- **Not that the premise is settled, only that it is sourced.** The Chinese-competition and
  Mexican-layoff story now has four dated notes in `Bibliotheca/` — including one that argues
  against it: VW's China position reversed for two months in early 2026 when EV subsidies expired.
  That reversal falls after the window the China leg of the test reads, and is exactly the kind of
  result that leg exists to catch, not evidence the premise is wrong before the test has even run.
  See `Bibliotheca/BIBLIOGRAPHY.md`, Part 1.
- **Not that the short can be run at scale.** Borrow cost, rebate and squeeze risk on a name with a
  small free float are a headline caveat, not a footnote.
- **Trial count: one.** This is the first idea tried in this repository.

## The seven questions, answered

| # | Question | Answer |
| --- | --- | --- |
| 1 | Why does the edge exist? | costly information plus continued drift after each disclosure, instead of an instant re-rating |
| 2 | Who is on the other side? | control holders and cap-weighted funds, who do not trade off a single disclosure |
| 3 | Risk premium or mispricing? | a mispricing claim; a risk-premium reading would have the short being paid for insurance, and the attribution step is what tells them apart |
| 4 | How many independent bets a year? | very few — three dated cases in the whole sample, not a recurring one; the weakest answer, and why a pass only justifies widening to more automakers' disclosures, not sizing up |
| 5 | Does it survive costs, and how much can it hold? | to be measured net; capacity is limited by borrow on a small free float |
| 6 | When does it fail, and would I hold through it? | when VOW3 re-rates in one jump right after either clean disclosure instead of continuing to drift; a squeeze on the short is the tail regardless of who is right |
| 7 | How many ideas before this one? | none |

**Where this stands, with every number and its caveats: [`RESULTS.md`](RESULTS.md).**
How work is done here, and the bar a result has to clear: [`AGENTS.md`](AGENTS.md).
