<h1 align="center">Game Theory Skill</h1>

<p align="center"><a href="README.md">中文</a> | English</p>

An AI skill pack for immediate use — it distills the equilibrium analysis tools in Drew Fudenberg and Jean Tirole's *Game Theory* into 16 capability cards that can be triggered individually or combined.

It is not a book summary, nor a reading response — it breaks the reusable methodology in the book into skill modules that can be triggered, executed and tested.

## What these skills solve

- Industry leaders issue a third round of price-increase letters and sign an output-cut pact — you cannot tell how many quarters this tacit pricing can hold, nor which link breaks first when the price war starts
- Faced with the same cost shock or demand slump, you cannot tell whether the industry competes on quantity or on price, where the price settles, or whether to follow this round of increases or grab share
- A company suddenly buys back stock, issues shares, cuts prices or expands capacity — you cannot read whether this is a costly, credible signal or zero-cost talk, nor how the market will read the announcement
- Management says it will "fight to the death and never cut prices" — you cannot score how long that statement still constrains behaviour, nor separate the words that would be said no matter what the real plan is, and are therefore zero-information
- Subsidy wars, loss-making expansion, sunset-industry shakeouts — you cannot judge who exits first, how long the bleeding lasts, or how much rent the contest has already dissipated
- How much to bid at an auction or a private-placement book-build, how to size the split and the deadline in a merger negotiation, why suppliers are asked for another price cut every year — there is no algorithm for reverse-engineering the other side's structure

## What was distilled

16 capability cards, organized in the order "model first, then competition and credibility, then transactions and information structure". 7 of them are promoted to standalone skills and 9 stay inside the routing entry, loaded on demand (per-card destinations are listed in [INDEX.md](./INDEX.md)):

- **Modeling foundations**: `industry-game-modeling-foundations` (count the effective players, pick an equilibrium concept on the timing × information grid, output a range rather than a point)
- **Competition and collusion**: `competition-pattern-comparative-statics` (competition-pattern discrimination and comparative statics), `collusion-price-war` (collusion sustainability and price wars: the δ threshold, punishment depth, horizon structure), `monitoring-cooperation-discipline` (monitoring structure and co-operation discipline: is a deviation attributable)
- **Credibility and signals**: `commitment-deterrence-credibility` (subgame-perfect tests of threats and commitments), `signal-reading-pbe` (the four-piece PBE reading: types / strategies / beliefs / responses), `reputation-tough-talk` (prior thresholds and geometric decay)
- **Timing and relationship assets**: `timing-war-attrition-preemption` (wars of attrition, pre-emption and exit: the L/F/B curve classification), `long-run-relationship-assets` (relationship rent versus the one-off gain from cheating)
- **Transactions and mechanisms**: `auctions-bidding`, `bargaining-durable-pricing` (bargaining shares and the Coase conjecture), `mechanism-reverse-engineering` (screening and information rents), `truthful-mechanisms-collective-action` (truthful mechanisms and collective action)
- **Equilibrium and information structure**: `multiple-equilibria-consensus`, `information-structure-common-knowledge`, `markov-state-variables`

Behind the 16 cards sit 338 candidates that passed triple verification (148 frameworks / 190 principles). Every card carries in-book worked examples (section A1) and boundaries (section B), so a judgement has a traceable source and does not overreach.

## Two packaging modes: single and pack

The same 16 capability cards are compiled twice, at two granularities. The content is identical; the only difference is how many entries an agent can discover.

| | single (one entry) | pack (compact pack, multiple entries) |
|---|---|---|
| Discoverable entries | **1**: `game-theory-skill` | **8**: one source router + 7 promoted standalone skills |
| Where the 16 cards live | All inside the entry's `references/capabilities/`, loaded 1–2 at a time by the router table | 7 cards become standalone skills; the other 9 stay in the router's `references/` |
| Triggering | Only the entry description participates in matching; routing happens after entry | The 7 high-frequency capabilities are matched directly, one hop fewer |
| Upgrades | Replace 1 directory | Replace 8 directories |

The 7 cards promoted to standalone skills in the pack:

- `collusion-price-war` — collusion sustainability and price-war analysis
- `signal-reading-pbe` — signal reading and dynamic incomplete-information analysis
- `commitment-deterrence-credibility` — commitment and deterrence credibility
- `competition-pattern-comparative-statics` — competition-pattern discrimination and comparative statics
- `timing-war-attrition-preemption` — timing competition: attrition, pre-emption and exit
- `long-run-relationship-assets` — brand, platform and long-run relationship assets
- `reputation-tough-talk` — reputation and tough talk

The 9 cards that are not promoted (`industry-game-modeling-foundations`, `monitoring-cooperation-discipline`, `auctions-bidding`, `bargaining-durable-pricing`, `mechanism-reverse-engineering`, `truthful-mechanisms-collective-action`, `multiple-equilibria-consensus`, `information-structure-common-knowledge`, `markov-state-variables`) stay in the router's `references/` and are reached through the routing entry — no capability is lost.

### Which one to install

Pick by the way you work, and **install only one**:

| How you work | Recommended | Why |
|---|---|---|
| You use DSH / Codex / Claude Code with a skills directory and want a clean list | single | Takes 1 slot, loses no capabilities |
| Your daily questions concentrate on "can this price increase hold / is this announcement a signal / does this statement count / who exits first / is this brand premium real" | pack | Those are exactly the promoted standalone skills, matched directly |
| You distribute to several agents or teammates who pick what they need | pack | They can install only the standalone skills they want |
| You want to install once and maintain one directory | single | Upgrades replace a single directory |

> Both builds come from the same bundle and carry identical capabilities. **Installing both will double-trigger**, so pick one.

## Examples

### Example 1: three rounds of price-increase letters — how long can this tacit pricing hold

**User question**

"Two cement leaders in East China have sent three rounds of price-increase letters, but capacity utilization is only 70%. How many quarters can this round of increases hold?"

**How the skill reasons**

- First run the modeling boundary in `industry-game-modeling-foundations`: this is repeated interaction (each period is isomorphic, history affects beliefs only) → repeated game, not a commitment or capital-accumulation model
- Enter `collusion-price-war` step 2, the horizon check: is there a public, certain expiry date? None → treat it as an infinite-horizon framework
- Step 3, identify the nature of the premium: first run the symmetric Cournot / Bertrand benchmark from the competition-pattern card and check whether a static oligopoly markup already explains the observed price — if you cannot separate the two, do not assume collusion
- Steps 4–5, compute the floor lines and the threshold: δ* = (max g − v) / (max g − post-punishment per-period profit); whether the punishment point uses the static equilibrium e or the minimax v̲ must be chosen and declared
- Step 6, estimate the real δ: funding cost + survival probability + repricing interval, three sources combined, as a range not a point; convert between annual and quarterly conventions before substituting
- Step 8, compare and stop: if the δ range and δ* do not overlap → "not sustainable"; if straddling → "conditionally sustainable" plus the list of flip factors

**Example final answer**

> The answer is conditionally sustainable, not "it holds". Three things have to be separated. First, the letter itself costs nothing and is not a commitment — what actually supports the price is the threat of being pushed back to competition after a deviation, so the judgement rests on δ, not on how often letters go out. Second, your 70% utilization means the one-period gain from deviating, max g, is large (idle capacity can fill the market at a discount at any time), which pushes δ* up; meanwhile funding cost and repricing interval pin down the range for the real δ. Compare the two: if the real δ is clearly below δ*, the correct expectation is that this round does not survive the next weak season; if it straddles, write down the flip factors — who deviates first, how big the demand shock is, and whether a certain endpoint is approaching (long-term contract expiry, new capacity coming online).
>
> Two inputs you have to supply. First, whether the post-punishment per-period profit uses e (static equilibrium) or v̲ (minimax) — a 0.05–0.10 difference is enough to flip a straddling verdict, so if you do not pick one and write it into your plan, the same data yields opposite conclusions. Second, if this industry only publishes market prices and not each player's shipments, the price war may not be a deviation at all but a discipline mechanism triggered by demand noise (the Green-Porter type): observing a price war is not observing a deviation. In that case switch to `monitoring-cooperation-discipline` and check whether the information structure allows attribution, instead of continuing to compute δ.

### Example 2: management says "we will never cut prices" — how long does that bind

**User question**

"The chairman said at the results call that the company will 'never join a price war and will fight to the death'. Does that count?"

**How the skill reasons**

- Enter `reputation-tough-talk` step 1, the cheap-talk filter: if he actually planned to cut prices, would he still say the same thing? Yes → the words themselves carry zero information
- Step 2, check the commitment-type support: does the market prior assign positive probability to a "fights to the death regardless of cost" type? Zero → the reputation mechanism fails and the flow stops
- Step 3, check observability: can rivals or investors see what he actually does? If not (say no entrant ever probes) → the type can never be revealed and the theorem does not apply
- Step 4, compute the threshold: the two-period version is p̄ = b/(b+1); period k's threshold is [b/(b+1)]^k, decaying geometrically; compare p⁰ with the threshold and back out the end-game collapse window
- Step 5, structural checks: is backing down reversible (only reversible concessions create multi-market amplification), and is information correlated (the flexibility cost of transparency)

**Example final answer**

> Split it into two layers. Layer one is the words themselves: the sentence holds for any real plan — he would say "fight to the death" even if he were preparing to cut, so the words have zero informational content and cannot be the basis of a judgement. What can bind behaviour is the reputation mechanism: whether the market gives a positive probability p⁰ to an "incorrigibly tough type", and how many periods are left to play.
>
> Layer two is the computation: let b be the payoff when the rival backs down; deterrence holds through the k-th period counted back from the end when p⁰ > [b/(b+1)]^k, with the threshold decaying geometrically. Mind the direction — k is the remaining number of periods counted back from the end, so p⁰ only suffices down to some period near the end; the last few periods are where deterrence fails and all earlier periods are credible. The formula therefore gives the **length of the end-game collapse window**, not "how many periods in total are credible"; reading it as the latter is exactly the directional error this card was caught on in stress testing and sent back for rework.
>
> Two common illusions to clear out first. One: "the group is large and tough across many markets, so a single-market threat is more credible" — in multi-market play where backing down is irreversible, the number of players cancels out and each market's equilibrium is identical to the one-on-one game, unless backing down is reversible (rivals can re-enter). Two: "the more often he says it, the more credible" — the binding force depends only on p⁰ and the remaining horizon, not on how often the statement is repeated. If you cannot estimate p⁰ at all, the correct move is to output a "prior × horizon condition table" (which range of p⁰ maps to which outcome), not to force a point judgement.

## How these skills were generated

This skill set was produced by the RIA-TV++ pipeline of **[cangjie-skill](https://github.com/kangarooking/cangjie-skill)**, in six stages:

1. **Whole-book comprehension (Adler analysis)** — Mortimer Adler's analytical reading method, breaking the book down through structure, interpretation, criticism and application
2. **Parallel extraction** — several specialized extractors (frameworks, principles, cases, counter-examples, terminology) work at once to pull candidate methodology units out of the text
3. **Triple verification** — every candidate must pass three tests: at least two independent in-book corroborations (cross-domain), the power to answer questions the book never states, and not being common sense (distinctiveness)
4. **RIA++ construction** — structure each unit along six dimensions: R (source quote) / I (restatement in our own words) / A1 (in-book case) / A2 (future trigger scenario) / E (executable steps) / B (boundaries and blind spots)
5. **Zettelkasten linking** — map dependencies, contrasts and combinations between cards, then generate the capability index and routing table
6. **Trigger and output testing** — design blind trigger tests for every card (including decoys: it must trigger when it should and stay silent when it should not) plus output evaluation scenarios; failing cards go back for rework and are regression-tested afterwards

Several book-specific decisions shaped the result: the original is a graduate-level theoretical textbook with almost no direct stock-market cases, so the "game concept → investment scenario" mapping is built by the cards themselves with self-declared parameters; theorem proofs and technical subsections (1.3, 3.3, parts of 5.5–5.6, the 7.6 appendix, 12.1, 13.3) do not become capabilities and are cited only as the basis of a card; the technical definitions of sequential equilibrium and trembling-hand perfection are folded into the reference layer of the credibility card rather than becoming a card of their own.

## Testing and verification

The test material ships inside the skill directories: 9 `test-prompts.json` files holding 107 cases (85 after de-duplication, since the 22 routing cases are the same file in `single/` and `pack/`'s router), plus a per-item scoring record in [test-results.md](./test-results.md) at the repository root.

- **Trigger cases, 63** (7 promoted cards × 9): 35 should_trigger, 21 should_not_trigger, 7 edge_case
- **Routing reachability cases, 22** (`game-theory-skill-router`): 16 should_trigger (route-U01…U16, one per capability card), 4 should_not_trigger, 2 edge_case
- **Blind trigger results**: a clean sub-agent blind run passed 81 / 85 (95.3%) in the first round, with all 4 failures being neighbour ambiguity rather than missing capability; after adding three pairs of neighbour-splitting clauses — fixing the skill, not the test — regression plus a full re-run reached 85 / 85 consistent with the updated descriptions (82 / 85 under the original expectations; both numbers are recorded side by side, the latter not used to hide the former)
- **Routing results**: 22 / 22 passed, with all 16 route questions landing on the expected card and all 4 irrelevant scenarios returning none
- **Output evaluation**: one representative task per card, 16 / 16 completed; spot checks of numeric conclusions match the book's theorems (δ* = 0.75, second-price bid = valuation, the 1/4 Myers-Satterthwaite threshold, geometric decay of the reputation threshold)
- **Rework**: all 16 cards were patched; `reputation-tough-talk` had one directional error (the critical period count obtained by inverting the geometric decay was read as "credible for 4 periods"; it was changed to the "end-game collapse window" reading)

## Repository structure

```text
game-theory-skill/
├── README.md               ← Chinese version
├── README.en.md            ← you are reading this
├── LICENSE                 ← MIT
├── BOOK_OVERVIEW.md        ← stage 0 output: Adler whole-book analysis
├── DIGEST.md               ← stage 5 output: reader-facing distilled long-form essay
├── INDEX.md                ← stage 3 output: skill map + dependencies
├── verified.md             ← 338 units that passed triple verification
├── TEST_SUMMARY.md         ← stage 4 output: stress-test summary
├── CANGJIE_ADAPTATION.md   ← cangjie adaptation notes
├── GITHUB_REPO.md          ← repository metadata
├── test-results.md         ← test result records
├── candidates/             ← stage 1 output: raw candidate pool
│   ├── frameworks.md       ← framework and method candidates
│   ├── principles.md       ← principle / rule / calculation candidates
│   ├── cases.md            ← case candidates from the book
│   ├── counter-examples.md ← counter-example and boundary candidates
│   └── glossary.md         ← terminology candidates
├── rejected/               ← stage 1.5 output: rejected units + reasons
├── bundle/                 ← compilation source of truth
│   ├── verified.yaml       ← capability metadata, criteria and destinations
│   ├── cards/              ← capability card sources (six sections)
│   └── book/               ← overview.md + glossary.md
├── single/                 ← single-mode build (one entry + all capability cards)
│   └── game-theory-skill/SKILL.md  ← entry: triggers + routing table + loading rules
└── pack/                   ← pack-mode build (one router + 7 promoted skills)
    └── */SKILL.md          ← 8 skills, each shipping a test-prompts.json
```

## How to use

Clone the repository first:

```bash
git clone https://github.com/raphael-y7/game-theory-skill.git
```

### Install single (try this first)

```bash
# macOS / Linux
cp -r game-theory-skill/single/game-theory-skill ~/.agents/skills/
```

```powershell
# Windows
Copy-Item -Recurse .\game-theory-skill\single\game-theory-skill "$env:USERPROFILE\.agents\skills\"
```

### Install pack

Copy only the directories that contain a `SKILL.md`; do not copy the two json files under `pack/` into the skills directory:

```bash
# macOS / Linux
cd game-theory-skill/pack
cp -r game-theory-skill-router \
      collusion-price-war \
      signal-reading-pbe \
      commitment-deterrence-credibility \
      competition-pattern-comparative-statics \
      timing-war-attrition-preemption \
      long-run-relationship-assets \
      reputation-tough-talk ~/.agents/skills/
```

```powershell
# Windows
$pack = ".\game-theory-skill\pack"
$dest = "$env:USERPROFILE\.agents\skills"
@('game-theory-skill-router','collusion-price-war','signal-reading-pbe','commitment-deterrence-credibility','competition-pattern-comparative-statics','timing-war-attrition-preemption','long-run-relationship-assets','reputation-tough-talk') |
  ForEach-Object { Copy-Item -Recurse -LiteralPath (Join-Path $pack $_) -Destination $dest }
```

> `~/.agents/skills` is the DSH skills directory; with another agent, use its own skills directory (for example `~/.claude/skills` for Claude Code).

### How to confirm it works

Ask "these two leaders have sent several rounds of price-increase letters, how many quarters can this round hold", and see whether the agent goes straight into the δ* computation of `collusion-price-war` (horizon check, then the nature of the premium, then floor lines and threshold, then compare and stop) instead of giving you generic industry-cycle talk. With single installed it reads the entry first and follows the routing table into a card; with pack installed the matching capability is hit directly.

## Source

- *Game Theory* by Drew Fudenberg and Jean Tirole

## Disclaimer

This repository publishes only the distilled skills, indexes and rule cheatsheets. It contains no PDF, EPUB, OCR files, screenshots or full transcript of the book. Quotations inside the capability cards serve only to cite the methodology's origin and keep the material auditable.

All numeric criteria in this repository (the critical discount factor δ*, the reputation threshold [b/(b+1)]^k, the 1/4 threshold for breakdown of trade, auction revenue equivalence, and so on) are computations of the theorems in special cases and inductions from teaching examples. Their validity rests on the assumptions that players are fully rational and the structure is common knowledge; the book provides no statistical backtesting support and gives no guarantee they hold in real markets. Test them against your own instruments and declare the conventions you use. Nothing in this repository is investment advice.

## License

[MIT](./LICENSE)
