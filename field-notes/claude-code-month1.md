# Claude Code, Month One

**Date:** 2026-05-12

The question going in was whether Max was worth it or just another subscription that didn't live up to the hype. So I went all-in on Claude Code for 30 days, three months into shipping a recovery support app. The real question wasn't whether it could help me ship. It was whether the help compounded.

---

## By the numbers

30 days. 363 commits. 201 PRs merged. 25 commit days inside a 31-day window. 11 product briefs. Three workflow docs doing the cross-session work: `WORK_LOG.md`, `docs/agent-memory.md`, `CLAUDE.md`.

More code in 30 days than the engineering teams I led at Science 37 would ship in a quarter. Same docs. Same tests. Same code-quality enforcement: line-count budgets on composition roots, mobile regression guards, an end-to-end harness. What's gone is the ceremony around it. No standups. No story points. No planning meetings to plan the planning. The trail in the repo is the artifact a Jira board would have been.

---

## What I shipped

Coming into the month, the codebase carried the mess of rapid prototyping. Features thrown at the wall to see what stuck.

The first stretch was de-spaghettifying the bits that stuck. A god-object context holding state for thirteen domains got extracted one at a time. Test scaffolding. An analytics pipeline so I could see what users actually did. A WebSocket refactor that swapped per-message scans for topic pub/sub. None of it features. All of it making features possible.

Then the two big surfaces, both rebuilt from tester feedback on the rough versions: a redesigned AI chat with audit logs and TTS, and a home page rebuilt around the daily ring. Then a four-day train of roughly 30 PRs that hardened the chat from "works in one session" to "holds a multi-day conversation." Pipeline split, persistent storage, history rehydration, cross-device sync, chain rotation to bound input cost.

The last stretch was the daily loop. Routine features end to end, plus an admin instrument that watches whether a user's morning routine actually happened. Verification framing in code, not just in a memo.

In parallel, design ran through Claude Design. A design system plus mockups for the home ring and the AI chat surface engineering shipped. The good news: the design system integrated back into the repo cleanly. The honest version: the last one-off mock I tried got scrapped out of frustration. Claude Design was a strong starting place for systems and a wobbly partner for novel layouts.

One refactor mid-month unified four separate chat experiences into shared primitives. Every chat-shaped feature from that day forward got cheaper. That's the kind of compounding I came into the month hoping for.

---

## Patterns I converged on

The pattern I kept coming back to: the repo is the memory.

**`WORK_LOG.md` started after I lost an hour.** Pulled up Claude on the home laptop after a productive day on the work laptop and watched the agent ask a question I'd answered the day before. Wrote three lines that night. Pulled them up next morning, agent read them in seconds, picked up where I'd left off. Not a feature. A habit I built around a missing one.

**`CLAUDE.md` grew the same way.** Every time I caught Claude trying to be clever in a way that bit me later, a new rule went in. "Don't be cute, don't be clever. Write the obvious code." "When build cost is about the same as test cost, build the real thing." Each rule settled an argument I never had to have again.

**`docs/agent-memory.md` was the third lane.** Less permanent rules, more breadcrumbs pointing forward. The line that drove a major shipping decision two weeks later was written first as a note to future-me: "if we can't verify it's happening, it's not happening."

**Lower-cost delegation.** Cheap models for first-pass drafts. Main thread for anything that touched verified behavior. Fan-out across worktrees when I could feel a reset coming.

**Briefs as breadcrumbs.** This is the move from my [intent-driven-exec playbook](../playbooks/intent-driven-exec.md), landing differently inside Claude Code. A brief in `docs/briefs/` was load-bearing only while the work was happening. The day after the PR shipped, the brief got a dated note at the top admitting what changed, and any durable rule moved into `CLAUDE.md`. The trail stayed. The blueprint did not.

---

## Where I hit walls

Three places I kept hitting the same wall.

**Cross-machine handoff is a hack, not a feature.** `WORK_LOG.md` works because I write it by hand and the model reads it by hand. There's no session-spanning state inside the tool. Every move between machines costs the same minutes: open a fresh session, watch the agent ask something I answered yesterday, paste in the work log, breathe.

**Cross-repo memory doesn't carry.** The marketing repo needs to share the privacy doc and the design system with the app. It knows about neither. The first time I had Claude work in the marketing repo, it wrote a privacy page from scratch and styled it from scratch, when both already existed one repo over. I caught it on review. The fix was manual: copy the docs over by hand, paste the design tokens, re-explain the house rules. There's no scope today for "these two repos share these assets." The gap shows up after, which is the wrong time to find it.

**Three surfaces, none of them aware of the others.** Claude Code for engineering. Cowork for chief-of-staff work. Claude Design for visual. All three from the same company. They share memory only through artifacts I move by hand: commits, screenshots, copied references. The same fact gets re-derived across all three, and I've watched them disagree about live state when one was reading a stale source.

---

## What would unlock me further

Two things.

**Cross-subset memory.** Between `CLAUDE.md` (permanent) and `WORK_LOG.md` (live state) is a missing layer: a scoped memory the agent maintains across sessions, addressable from any machine, writable from any Anthropic surface, sharable across a subset of repos. Today I do this by hand. A first-party version closes the cross-machine wall, the cross-repo wall, and the cross-surface wall in one move.

**A trail surface, not a chat surface.** The CLI is conversational by default. The durable value I got this month came from artifacts that survived the conversation: commits, briefs, memory entries, work log, screenshots. A first-class trail view, scoped per repo, that an agent reads at session start and writes during the work. Think `git log` for context, with the agent as a contributor.

Neither is a new idea. Both are versions of moves I'm already making outside the tool. Either one buys me another gear.

---

## Closing

Claude Code's edge isn't speed. The edge is context. Speed comes free when the context is right. It disappears when context drifts. The receipts say the same.

---

*How this was assembled: data extracted by Claude Code (git log, gh CLI, repo grep), synthesis written against the receipts, fact-checked against the data dump before commit.*
