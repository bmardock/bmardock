# 04 — Scorecard System

## When to pull this out

When you want to lead with clarity instead of reacting to confusion. Start Day 0—not mid-quarter when expectations are already set.

## Why it matters

Great teams define their own success metrics and tell their story with data. When you own the scorecard, you can focus energy on what actually moves the needle instead of optimizing for someone else's incomplete picture.

---

## Inputs (Start where you are)

- Your vision or roadmap
- Current dashboards or rituals (even the imperfect ones)
- Commitment to improving your data quality along the way

**First checkpoint:** If you can't measure it now, that's your first win opportunity—fix the measurement, then track the improvement.

---

## Core Steps (Quick to set up, built to stay alive)

1. **Pick 3–5 sharp metrics**

   - Mix **leading** indicators (what you can influence today) with **lagging** ones (scoreboard results). Leading metrics are your steering wheel.

2. **Write them as headlines**

   - Make them memorable and actionable:
     `Lead Time — ≤ 14 days (sprint to ship)`
     `Trade-off Clarity — ≥ 90% documented (decisions that stick)`

3. **Build for what counts now**

   - Start tracking immediately, even if imperfect. You can refine as you go.

4. **Embed in existing rhythms**

   - Stand-ups, retros, leadership syncs—weave metrics into conversations that already happen.

5. **Weekly momentum check**: What's accelerating, what's stuck, what breakthrough do you need?

6. **Quarterly WAR (Wins, Actions, Requests)**

   - **Wins:** What's trending up that we should celebrate and amplify?
   - **Actions:** What's not working, and what's our next experiment?
   - **Requests:** What support would unlock the next level of performance?

## Implementation Steps

### Week 1: Baseline

- Gather historical data for chosen metrics
- Set up automated tracking where possible
- Document manual collection processes
- Establish "good/concerning/bad" thresholds

### Week 2-3: Track & Adjust

- Collect data consistently
- Identify measurement challenges
- Refine thresholds based on actual data
- Start weekly check-ins during standups

### Week 4+: Review & Experiment

- Analyze trends and patterns
- Propose experiments when metrics drift
- Celebrate improvements and learn from setbacks
- Adjust metrics that aren't driving valuable behavior

## Evidence Formats

**Dashboard Links:**

- Grafana/DataDog performance metrics
- Jira/GitHub velocity and quality reports
- CI/CD success rates and build times

**Qualitative Signals:**

- Team survey results (monthly pulse)
- Customer feedback themes (support tickets)
- Code review quality assessments

**Documentation Artifacts:**

- ADR completion rates
- Onboarding feedback and time-to-productivity
- Knowledge sharing session frequency

## Review Meeting Template (30 minutes)

### Check-in (5m)

- Any metrics that need immediate attention?
- Data collection challenges or missing information?

### Trend Analysis (15m)

- What's improving and why?
- What's concerning and what might be causing it?
- Any external factors affecting our metrics?

### Experiment Planning (10m)

- What should we try differently?
- Who will own the experiment?
- How will we know if it's working?

---

## Avoid These Traps (Keep the energy high)

- **Metric overload:** Too many metrics scatter focus. Pick the vital few that actually drive decisions.
- **Set-and-forget dashboards:** Metrics without regular conversation become wallpaper. Keep them alive with weekly check-ins.
- **Numbers without story:** Data needs context to drive action. Always pair trends with narrative.
- **Gaming behaviors:** When metrics become targets, add qualitative balance. Track both outcomes and the behaviors that create them.

## Built for Everyone (Rookie to Master)

- **For the rookie:**

  - Start with 2-3 simple metrics, focus on building the habit of regular review, use visual dashboards and clear "why this matters" context.

- **For the master:**

  - Layer in confidence intervals, leading/lagging relationships, and proxy signals. Use metrics to spot patterns and drive strategic experiments.

## Sample Scorecard — Q3 (Your Team)

```markdown
| Metric                    | Target | Current | Trend  |
| ------------------------- | ------ | ------- | ------ |
| Lead Time (days)          | ≤ 14   | 18      | ↘ +20% |
| % Decisions w/ Trade-offs | ≥ 90%  | 75%     | ↗      |
| Rework Rate (%)           | ≤ 10%  | 12%     | ↘      |
| Clarity (1–10)            | ≥ 8    | 6.5     | ↗      |

**Wins:** Trade-off docs moving up—team's getting better at documenting decisions
**Actions:** Auto-flag PRs without trade-offs—make good habits easier
**Requests:** If lead time hits 21 days, escalate blockers to leadership
```

## Metrics / Scorecard

**Meta-metrics for the scorecard system itself:**

- **Data quality:** % of metrics collected consistently
- **Team engagement:** Participation in reviews and experiments
- **Decision influence:** # of changes made based on scorecard insights
- **Predictive value:** How well metrics predict actual problems

## Example Experiments

**When sprint goal hit-rate drops:**

- Experiment: Add 20% buffer to sprint planning
- Timeline: 2 sprints
- Success criteria: Hit-rate >80% without reducing scope

**When tech debt ratio climbs:**

- Experiment: Reserve 1 story per sprint for tech debt
- Timeline: 1 month
- Success criteria: Ratio trends downward, team velocity stable

**When bug kickback rate rises:**

- Experiment: Require demo video for UI changes
- Timeline: 3 weeks
- Success criteria: Kickback rate <15%, team feedback positive

## References

- [Operating System playbook](./03-operating-system.md) for the foundation pillars
- [Sprint Planning playbook](./07-sprint-planning-retros.md) for incorporating metrics
- [Google's DORA metrics](https://cloud.google.com/blog/products/devops-sre/using-the-four-keys-to-measure-your-devops-performance)
- [Accelerate book](https://itrevolution.com/accelerate-book/) on high-performing teams
