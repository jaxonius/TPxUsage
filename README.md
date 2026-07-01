# TPx Usage — Claude Seat Allocation & Budget Model

An interactive model and strategy for allocating a ~$60K/year Claude budget across ~50 seats with a phased, value-weighted rollout.

## Files

- **[claude-seat-budget-model.html](claude-seat-budget-model.html)** — Interactive budget allocator
  - Toggle phase presets (Broad Baseline → Tier & Upgrade → Concentrate)
  - Adjust per-tier headcount and seat types (Premium / Standard / Reclaimed)
  - Compare Claude Team vs. Enterprise pricing
  - Live cost calculation against a $60K budget
  - Dark-mode responsive design, works offline from Drive

- **[STRATEGY.md](STRATEGY.md)** — Durable text reference
  - Verified Claude pricing (claude.com/pricing, 2026-06)
  - Three-phase rollout with gating criteria (usage-based, not calendar-based)
  - Per-personnel allocation chart (default tier split)
  - Value measurement framework (weekly-active %, PR throughput, DXI)
  - Top risks and boundary notes
  - Full source citations

## Quick start

Open `claude-seat-budget-model.html` in any browser. The model is self-contained and works offline.

### Phase presets (one-click scenarios)

1. **Phase 1 · Broad baseline** — All 50 on Standard (~$12K/yr; ~$48K uncommitted)
2. **Phase 2 · Tier & upgrade** — 10 Power (Premium) + 15 Steady + 20 Light (Standard) + 5 Dormant (Reclaimed)
3. **Phase 3 · Concentrate** — 20 Power (Premium) + 15 Steady (Standard) + 10 Light (Standard) + 5 Dormant (Reclaimed)
4. **Ceiling · All premium** — 50 Premium seats = exactly $60K/yr

### Key insight

AI usage is a power law. A handful of power users drive most value; a long tail barely logs in. Rather than guessing the allocation up front, release everyone on **Standard** ($12K/yr for 50) and let "hitting the limit" be your upgrade signal. **You likely won't spend all $60K—that's correct.** Hold the gap for extreme-tail users and expansion.

## The vehicle: Claude Team (not Enterprise)

- **Team Standard**: $240/seat/yr ($20/mo annual) · Pro-level Claude Code usage · 50 × $240 = $12K
- **Team Premium**: $1,200/seat/yr ($100/mo annual) · 5× usage · for revealed power users
- **Team total cap**: 150 seats, SSO/SCIM/analytics included, no per-token surprises

**Why not Enterprise?** Enterprise unbundles tokens (2026 model): ~$20/seat + all usage at API rates = **~$150–250/dev/month in metered cost**. For 50 active devs, that's **$90–150K/yr in usage alone** — far past $60K. Enterprise only wins if per-user spend caps / audit / CMEK are mandatory requirements.

## Phased rollout (gating is usage/cost-based, not calendar-based)

### Phase 1 — Broad baseline (wks 1–6)
- All 50 on Standard (~$12K/yr).
- Turn on usage analytics, ship shared `CLAUDE.md`.
- Managers actively encourage use (7× more daily users when encouraged).
- **Gate to Phase 2:** Someone hits their Standard limit *or* aggregate spend pace hits ~$20K/yr.

### Phase 2 — Tier & upgrade (the reassessment)
- Upgrade users who hit the limit to Premium (+$960/yr each).
- Reclaim dormant seats (<1 session/week).
- **Gate to Phase 3:** Cost-per-active-dev within forecast; weekly-active ≥70% of provisioned seats.

### Phase 3 — Concentrate & guardrail (month 4+)
- Push budget to proven tail; reserve for 1–2 outliers beyond Premium.
- Assign a **permanent owner** (~10% of one engineer) running **monthly reclaim-and-redeploy** cycles.
- Keep dormancy <10%.

## Measure value honestly

Anchor decisions to **weekly-active % + PR throughput + time-saved/DXI**, computed **per tier, not per head**.

⚠️ **Distrust self-reports.** The METR RCT found experienced devs were **19% slower** with AI yet believed they were ~20% faster. Use measured PR/DORA data, not surveys.

### Leading indicators
- Weekly-active users (target 60–70%)
- % of PRs that are AI-assisted
- Code-review turnaround (target 20–30% reduction)

### Lagging indicators
- PR throughput & tasks completed
- DORA outcomes (lead time, change failure rate <15%)
- Developer Experience Index (DXI) / satisfaction
- Change-failure-rate alongside speed (2025 DORA: AI lifts throughput but hurts stability without strong tests/CI)

## Top risks

1. **Treating seat = total cost.** True on bundled Team; false on Enterprise (tokens are extra).
2. **Flat allocation across a power law.** ~20% drive most consumption—cap and concentrate by tier.
3. **Over-provisioning without reclaim.** Don't pay for logged-out users; reclaim monthly.
4. **No permanent owner.** Rollouts handed to a disbanding team stall and bleed budget.
5. **Chasing vanity metrics** (lines-of-code, % AI-generated, monthly-active).

## Sources

- [claude.com/pricing](https://claude.com/pricing) — Live Claude plans (verified 2026-06-27)
- [Claude Enterprise Plan](https://support.claude.com/en/articles/9797531-what-is-the-enterprise-plan) — Unbundled usage-based billing
- [Claude Code Costs](https://code.claude.com/docs/en/costs) — Rate limits, usage per tier, workspace spend/rate limits
- [Systemprompt.io Rollout Guide](https://systemprompt.io/guides/claude-code-organisation-rollout) — 4-phase design, gating criteria, weekly-active thresholds
- [Faros Adoption Guide](https://www.faros.ai/blog/enterprise-ai-coding-assistant-adoption-scaling-guide) — Launch-Learn-Run timeline, tier splits, champions
- [DX Measurement Framework](https://getdx.com/research/measuring-ai-code-assistants-and-agents/) — Leading/lagging indicators, utilization/impact/cost
- [METR RCT](https://metr.org/blog/2025-07-10-early-2025-ai-experienced-os-dev-study/) — Perceived vs. actual performance gap
- [DORA 2025](https://dora.dev/dora-report-2025/) — AI throughput gains + stability tradeoff

---

**Built:** 2026-06-27 | **Budget:** ~$60K/year | **Seats:** ~50 | **Vehicle:** Claude Team (Standard + Premium mix)
