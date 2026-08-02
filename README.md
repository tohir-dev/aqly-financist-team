# Financist Team — 8-lens finance analysis for Claude

A finance question rarely has one right answer — it has a theoretical answer, a numerical answer, an
empirical answer, and a risk answer, and they often disagree. This skill turns Claude into an
orchestrator that routes your question to the right **methodological lenses**, runs them in parallel
as independent subagents, and reconciles them into one cited answer that *shows where the experts
disagree* instead of papering over it.

## What's in the box

| Agent | Lens | Encoded practice of |
|---|---|---|
| `finance-theoretician` | No-arbitrage, CAPM/APT/SDF, assumption stress tests | Markowitz, Sharpe, Modigliani-Miller, Black-Scholes-Merton, Ross, Lucas, Hansen, Cochrane, Duffie |
| `finance-quant` | Derivative pricing, vol surfaces, Monte Carlo / PDE / FFT, hedging | Hull, Heston, Carr, Gatheral, Rebonato, HJM, Longstaff-Schwartz |
| `finance-empiricist` | Factor tests, backtests, ML-for-returns, event studies | Fama, French, Engle, Kelly, Xiu, Harvey, López de Prado, Pedersen |
| `finance-risk` | VaR / ES / EVT tails, robust allocation, stress and systemic risk | Embrechts, Meucci, Engle (SRISK), Brunnermeier (CoVaR) |
| `finance-behavioral` | Bias audits, sentiment, choice architecture, bubble diagnostics | Kahneman, Tversky, Thaler, Shiller, Barberis, Odean-Barber, Sunstein |
| `finance-macro-policy` | Central banking, early-warning indicators, sovereign and bank stability | Diamond-Dybvig, Bernanke, Reinhart-Rogoff, Rey, Gorton, Shin, Borio, Admati |
| `finance-execution` | Optimal execution, market impact, order book, TCA | Almgren-Chriss, Kyle, O'Hara-Easley |
| `finance-corporate` | WACC, DCF/EVA, capital structure, M&A, LBO | Modigliani-Miller, Jensen, Myers, Rajan-Zingales |

Plus `SKILL.md` — the orchestrator: routing rules, parallel dispatch, a synthesis contract, and a
hard advisory guardrail.

## Install

**Importing from GitHub** (marketplaces, or any skill importer that takes a URL) — paste
**this** URL. It points at the folder that contains `SKILL.md`, which is one level below the
repo root:

```
https://github.com/tohir-dev/aqly-financist-team/tree/main/financist-team
```

> ⚠️ The bare repo URL (`https://github.com/tohir-dev/aqly-financist-team`) will **not** work —
> there is no `SKILL.md` at the repo root.

**Installing manually** — clone or download the repo, then copy the inner
**`financist-team/`** folder (not the `aqly-financist-team` repo folder — the skill directory name must
match the `name:` in `SKILL.md`).

**Project scope** — available in one repo:

```bash
mkdir -p .claude/skills && cp -R financist-team .claude/skills/
```

**Personal scope** — available everywhere:

```bash
mkdir -p ~/.claude/skills && cp -R financist-team ~/.claude/skills/
```

Then start Claude Code and ask a finance question, or invoke the skill by name.

**Optional speedup.** The orchestrator dispatches agents by reading `agents/*.md` and inlining them,
so the skill works with no further setup. If you'd rather have them as native subagent types:

```bash
mkdir -p .claude/agents && cp financist-team/agents/*.md .claude/agents/
```

## Try it

```
Price a 1-year European call on a non-dividend stock under Heston, and tell me
how much of the price is model choice rather than market data.
```

```
Our board wants to lever up to buy back stock. Walk me through what actually
changes and what the failure modes are.
```

```
Is the low-volatility anomaly real, or is it a multiple-testing artifact?
```

The orchestrator picks the lenses, tells you which ones it picked and why, runs them concurrently,
and returns a single answer with a consensus-and-disagreement section.

## Design commitments

- **Verification is mandatory.** Numerical results are cross-checked against a second method.
  Empirical claims need out-of-sample testing and a multiple-testing correction.
- **Assumptions first.** Every price or conclusion states what it rests on.
- **Disagreement is surfaced, not smoothed.** EMH vs behavioral, monetary vs macroprudential — the
  answer shows the split.
- **Sources are preserved.** A finding without a source is flagged as unverified.
- **Actionable numbers carry an as-of date** or are explicitly labeled `UNVERIFIED`.

## Scope boundary (important)

This skill produces **educational and analytical output. It is not personalized investment advice.**
It is built to refuse — on every question, not just ones flagged "personal" — to emit market-timing
calls, directional price forecasts, or a specific portfolio allocation as its answer. On a personal
buy/sell/hold question it gives scenarios and decision factors, names what it would need to tailor
the analysis, and points you to the right kind of licensed professional. Licensed investment advice,
binding tax or legal conclusions, and trade execution are out of scope by design.

If you want a tool that tells you what to buy, this is the wrong tool.

## Requirements

- Claude Code (or any Claude client that supports skills and subagent dispatch).
- No API keys, no external services, no dependencies. Everything is Markdown.
- `finance-quant`, `finance-empiricist`, `finance-risk`, `finance-execution`, and
  `finance-macro-policy` will use `Bash` for numerical work when it's available.

## License

See [LICENSE](LICENSE).

---

### Part of Aqly Skills

Six other standalone multi-agent skills for Claude Code, each sold separately:

- [software-team](https://github.com/tohir-dev/aqly-software-team) — 40-agent software company
- [research-team](https://github.com/tohir-dev/aqly-research-team) — 20-archetype research org
- [analyst-team](https://github.com/tohir-dev/aqly-analyst-team) — business-intelligence org
- [sales-team](https://github.com/tohir-dev/aqly-sales-team) — 17-role revenue engine
- [marketing-team](https://github.com/tohir-dev/aqly-marketing-team) — 15-agent marketing agency
- [production-readiness](https://github.com/tohir-dev/aqly-production-readiness) — launch-blocker gate
