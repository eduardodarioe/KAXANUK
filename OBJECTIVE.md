# Objective

> **Step 1 of 8, with `Bibliotheca/`.** One idea, one objective, and the claims inside it with
> their status. Written before any return was looked at: the only market data touched so far is
> average daily volume, used to set the liquidity floor of the universe.

## The objective, in one paragraph

**The claim:** Volkswagen preferred shares (`VOW3.DE`) earn less than an equal-weighted basket of
the other liquid Xetra automakers (`BMW.DE`, `MBG.DE`, `CON.DE`) over holding periods of three to
twelve months, net of costs. **Its source of edge** is behavioral under-reaction together with
limits to arbitrage: the damage from Chinese competition and from plant cuts, including the
reported job losses at the Mexican plants, arrives in reported margins slowly and in steps, prices
anchor on a low earnings multiple and a dividend yield, and the ones who could act on it are
constrained. The door is still open only if that deterioration reaches prices later than it reaches
the accounts, which is the thing being tested and not something assumed. **The other side** is the
holder who is not trading on return: the Lower Saxony state and the Porsche and Piech families
hold the voting control for reasons of control, index and cap-weighted funds hold VW by market
value and do not rebalance on margin trend, and short sellers face a thin free float, the squeeze
history of 2008 and borrow cost. **The test**, fixed now: the monthly return of a book that is
short `VOW3.DE` and long an equal-weighted basket of `BMW.DE`, `MBG.DE` and `CON.DE`, rebalanced
monthly, priced net of commission and with a stated borrow cost, measured over 2016 to 2026 and
split into three sub-periods, 2016 to 2019, 2020 to 2022 and 2023 to 2026, then passed through
attribution to see whether what remains after market and factor exposure is different from zero.
**The kill switch:** if the spread is not positive net of costs in at least two of the three
sub-periods, or if attribution assigns it to market beta or to a known factor instead of to VW
itself, the idea is abandoned and not re-tuned.

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
parameters. Complexity, such as generalising the rule to the whole universe by a margin-trend
signal, is added one lever at a time, and each addition must beat this baseline to earn its place.

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
| **2. The mechanism** | the gap comes from margins that deteriorate before the price does, not from the car cycle | **untested** |
| **3. The construction** | equal weight against a fixed basket removes exposure to the market and to Germany's cycle | **true by construction, untested as a source of return** |

## What is not claimed

- **Not that the parameters are right.** There are none to tune: the peer set, the horizon and the
  sub-periods are set here, before any return is seen. That is a defence against data-snooping and
  not evidence of optimality.
- **Not that this is out of sample.** Nothing is until an experiment reaches step 7.
- **Not that this is statistically decisive.** One name against a basket is a small number of
  independent bets a year, and a ten-year sample of it is a case study. It can reject the idea; it
  cannot make it certain.
- **Not that the premise is settled, only that it is sourced.** The Chinese-competition and
  Mexican-layoff story now has four dated notes in `Bibliotheca/` — including one that argues
  against it: VW's China position reversed for two months in early 2026 when EV subsidies expired,
  which is a candidate trigger for the kill switch's "recovery in China" scenario, not evidence the
  premise is wrong. See `Bibliotheca/BIBLIOGRAPHY.md`, Part 1.
- **Not that the short can be run at scale.** Borrow cost, rebate and squeeze risk on a name with a
  small free float are a headline caveat, not a footnote.
- **Trial count: one.** This is the first idea tried in this repository.

## The seven questions, answered

| # | Question | Answer |
| --- | --- | --- |
| 1 | Why does the edge exist? | costly information plus slow pass-through of deterioration into anchored prices |
| 2 | Who is on the other side? | control holders and cap-weighted funds, who do not trade on margin trend |
| 3 | Risk premium or mispricing? | a mispricing claim; a risk-premium reading would have the short being paid for insurance, and the attribution step is what tells them apart |
| 4 | How many independent bets a year? | very few; this is the weakest answer and the reason the rule is generalised only after it passes |
| 5 | Does it survive costs, and how much can it hold? | to be measured net; capacity is limited by borrow on a small free float |
| 6 | When does it fail, and would I hold through it? | when a recovery in China or a restructuring re-rates VW; a squeeze on the short is the tail |
| 7 | How many ideas before this one? | none |

**Where this stands, with every number and its caveats: [`RESULTS.md`](RESULTS.md).**
How work is done here, and the bar a result has to clear: [`AGENTS.md`](AGENTS.md).
