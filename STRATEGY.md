---
title: "6. TPx — Claude Seat Rollout Strategy"
purpose: One-page strategy for allocating a ~$60K/yr Claude budget across ~50 seats — phased, value-weighted, with the per-personnel allocation chart.
domain: 6. TPx
updated: 2026-06-26
confidence: Team pricing high; Enterprise seat base medium; tier %s are planning defaults (replace with Phase-1 data)
---

# Claude Seat Rollout — 50 seats, ~$60K/yr

> 🎛️ **Interactive model:** [6. TPx — Claude Seat Budget Model.html](<6. TPx — Claude Seat Budget Model.html>) — toggle tiers, seat prices, budget, and phase presets live (canonical; mirror at `Master Outputs/6. TPx/Claude Seat Budget Model.html`). This `.md` is the durable text twin.

**The decision in one line:** Buy **Claude Team** (mix-and-match seats), release everyone on **Standard** first, then spend the budget *upgrading the revealed power users to Premium* — don't guess the allocation up front, let usage data reveal it.

**Why this shape:** AI usage is a power law. The seat is cheap; the 5× **Premium** upgrade is the expensive lever. 50 Standard seats = **$12K/yr**; 50 Premium = **$60K/yr exactly**. So the whole budget question reduces to *how many people earn the upgrade* — which Phase 1 answers with data instead of guesswork. (Anchor: one extreme power user — Jackson's own Claude Code — generated ~$13K of API-equivalent value in a quarter, far past even a Premium seat. The tail is where the value is.)

## Plan vehicle (verified vs claude.com/pricing, 2026-06)

| Plan | Cost | Claude Code | Admin | Fit |
|---|---|---|---|---|
| **Team — Standard** | **$240/seat/yr** ($20/mo annual) | ✅ Pro-level usage | SSO, SCIM, usage analytics, audit logs | Default for everyone |
| **Team — Premium** | **$1,200/seat/yr** ($100/mo annual) | ✅ **5× usage** | same | Revealed power users |
| Enterprise | ~$20/seat + **tokens billed separately at API rates** | ✅ unbundled | + per-user $ spend caps, CMEK, Analytics/Compliance API | ⚠️ Wrong fit at this budget — 50 active devs ≈ **$90–150K/yr in usage alone**. Only if per-user spend caps / audit / CMEK are mandatory. |
| Pro / Max | $20 / $100 / $200 mo | ✅ | **none** (individual accounts) | ❌ No admin console — can't manage 50 seats |

Team lets you blend Standard + Premium in one org (5–150 seats). **High confidence** on Team prices; the Enterprise ~$20 base is **medium** (Anthropic says "contact sales").

## Three phases (gates are usage/cost-based, not calendar-based)

**Phase 1 — Broad baseline (wks 1–6).** All 50 on **Standard** (~$12K/yr run-rate; ~$48K uncommitted). Turn on usage analytics, ship a shared `CLAUDE.md`, and have managers *actively encourage* use — the single biggest lever (devs at encouraging orgs are **7× more likely** to be daily users). Don't judge before ~wk 4: individual ramp is ~2 wks, org steady-state is 3–4 months.

**Phase 2 — Tier & upgrade (the reassessment).** Trigger = *someone hits their Standard limit, or aggregate pace climbs.* Hitting the limit **is** the value signal — upgrade those users to Premium (+$960/yr each); reclaim dormant seats. Expect ~60–70% weekly-active **at best**, so plan for 30–40% under-used.

**Phase 3 — Concentrate & guardrail (month 4+).** Push budget toward the proven tail; reserve headroom for the 1–2 outliers who exceed even Premium (raw usage-based API). Assign a **permanent owner** (~10% of one engineer) running a **monthly reclaim-and-redeploy** cadence to keep dormancy < 10%. That recurring discipline — not the day-one buy — is what protects the budget.

## Per-personnel allocation chart (planning default → replace with Phase-1 data)

| Tier | ~% | Seats | Seat type | $/yr each | Tier total | Promote / value signal |
|---|---|---|---|---|---|---|
| **Power** | 20% | 10 | Premium | $1,200 | $12,000 | Hits Standard limit · daily · high PR throughput |
| **Steady** | 30% | 15 | Standard | $240 | $3,600 | Weekly-active · solid value |
| **Light** | 30% | 15 | Standard | $240 | $3,600 | Sporadic · re-onboard before reclaiming |
| **Dormant** | 20% | 10 | Reclaim | $0 | $0 | < 1 session/wk · pull seat |
| **Total** | | 40 paid | | | **≈ $19,200/yr** | Leaves a large deliberate reserve under $60K |

Scenario range: Phase 1 all-standard **$12K** · recommended mix **~$20K** · aggressive (20 Premium) **$30K** · ceiling all-Premium **$60K**. **You likely won't spend all $60K — that's correct.** Hold the gap for the extreme tail + expansion; don't spend it to "use it up."

## Measure value honestly

Anchor budget decisions to **weekly-active % + PR throughput + time-saved/DXI moving together** — computed **per tier, not per head**. Distrust vanity metrics (lines-of-code, "% AI-generated," monthly-active) and **self-reports**: the METR RCT found experienced devs were **19% slower** with AI yet believed they were ~20% faster. Track change-failure-rate alongside speed (2025 DORA: AI lifts throughput but hurts stability without strong tests/CI).

## Top risks

1. **Treating seat = total cost.** True on bundled Team; *false* on Enterprise (tokens extra). Don't drift to Enterprise without budgeting metered usage.
2. **Flat allocation across a power law.** ~20% drive most consumption/value — cap and concentrate by tier, don't average.
3. **Over-provisioning / dormancy.** Buying 50 seats up front guarantees waste; reclaim, don't pay for logged-out users.
4. **No permanent owner.** Rollouts handed to a disbanding team stall and bleed budget to dormant seats.

## Boundary & sources

- **OneDrive boundary:** this is the durable *strategy* record. Any live seat-tracking / actuals workbook belongs in `~/Library/CloudStorage/OneDrive-TPxCommunications/` (Core Rule 1 — don't write working files here).
- **Sources:** [claude.com/pricing](https://claude.com/pricing) · [Enterprise plan (support)](https://support.claude.com/en/articles/9797531-what-is-the-enterprise-plan) · [Claude Code costs/limits](https://code.claude.com/docs/en/costs) · rollout & metrics: [systemprompt.io rollout guide](https://systemprompt.io/guides/claude-code-organisation-rollout), [Faros adoption guide](https://www.faros.ai/blog/enterprise-ai-coding-assistant-adoption-scaling-guide), [DX measurement framework](https://getdx.com/research/measuring-ai-code-assistants-and-agents/), [METR RCT](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/), [DORA 2025](https://dora.dev/dora-report-2025/).

## Up

- [MASTER_CONTROL](<../0. Master Control/MASTER_CONTROL.md>) — vault kernel
- [TPx Master](<TPx Master.md>) — domain hub
