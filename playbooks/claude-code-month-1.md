# Claude Code, Month One

**Written:** 2026-05-12 · **Published:** 2026-07 (postscript added)

A working retro from a solo founder shipping a recovery app. What landed, what didn't, where the surface ends today. Receipts in the repo, not in the prose.

*(A note on the receipts: the app repo is private, it holds a recovery community's data and stays that way. PR numbers and file paths below are cited as they exist there; every count comes straight from its git log.)*

---

## By the numbers

A Tuesday in mid-April I opened a fresh terminal pane and decided I would try running every commit through Claude Code for thirty days, no exceptions.

The month closed on 2026-05-12. The shape of it:

- **358 commits** on `main`, **193 squash-merged PRs**, on a recovery app called Fellowship. The full list is one `git log --since=2026-04-12 --until=2026-05-12` away on my side.
- **11 product briefs** filed under `docs/briefs/` (the breadcrumb folder, not the blueprint folder).
- **3 workflow docs** that did the cross-session lifting: `WORK_LOG.md`, `docs/agent-memory.md`, `CLAUDE.md`.
- **1 repo** covered end to end. A second smaller repo for my profile and playbooks (`bmardock/bmardock`) drafted in worktrees off the same harness.

That is the scale. The interesting part is what happened to my workflow underneath it.

---

## What I shipped

Five representative pieces, one sentence each on what the user gets:

**Sponsor v1 stabilization train.** A roughly thirty-PR sweep between #114 and #156, turning a flaky AI-fellow chat into something with durable history, cross-device sync, cost-bounded turns, and a working idle-check-in pattern. What it unlocks: my cofounder Cory now has multi-day usage on it, which is the first time the daily loop has held for anyone but me.

**Off-circle reach-outs + admin Routine tab.** #240 shipped two things at once: a way to log a call to a sponsor who isn't in the app, and a read view that shows whether a user's morning ritual actually happened. What it unlocks: the verification framing in code, not just in a memo.

**Daily Pages.** A voice-dictation morning practice that drains the noise before the day starts. Built across #170, #172, #175, #176, #177. What it unlocks: a prevention layer for users who want one, with the transcript stored privately and never read back.

**Meetings scraper fallback.** #100 replaced a broken third-party API with a local scraper plus a richer detail screen and GPS. What it unlocks: a user in early recovery can find an in-person meeting near them without the page being broken.

**Milestone share cards.** #134, #165, #168. Open Graph cards with the user's day count, designed to land cleanly in iMessage. What it unlocks: a user celebrating thirty days can share it without exposing identity, and the recipient can tap through to a sober-curious landing page.

None of these would have surprised a co-worker who watched me ship. They surprised me only in that I shipped all five in the same month, alone.

---

## Patterns I converged on

The pattern that mattered most was treating the repo as the memory layer.

I started the month using Claude Code the way most people probably do: one terminal, one repo, ask, accept, commit. By week two I was working on three machines and losing context between them. The fix was small and not clever:

**`WORK_LOG.md` as cross-machine handoff.** A flat markdown file at the repo root with three sections: In Progress, Next Up, Recently Completed. Updated at the end of every session, read at the start. The header literally says "Stale log = wasted ramp time." Pull, read, work. The agent gets the same five minutes of orientation I would have wanted, in fifteen seconds.

**`CLAUDE.md` as rules accumulator.** Every time I caught the model doing something I wanted it not to do, the rule went in `CLAUDE.md`. "Don't grow `AppContext.tsx`." "Composition roots have line-count budgets enforced in `scripts/check-line-budgets.sh`." "When build cost equals test cost, build the real thing." The file became a contract I didn't have to renegotiate. Anyone reading it, including future me, knows the rules of the house.

**`docs/agent-memory.md` as forward-pointing notes.** Different shape from `CLAUDE.md`. The rules file is permanent; the memory file is provisional. It carries the live state of the project and, more important, the breadcrumbs that point the next session forward: "Don't add new tz-aware endpoints without also wiring the heal call." Read like a note an engineer left for the next shift.

**Fan-out near reset windows.** I learned to spawn three or four worktrees in the last hour before a context reset, each with a different exploration brief, then pick the one that landed. The `.claude/worktrees/` directory at the end of the month had nine drafts of the same playbook because that is what exploring looks like when execution is cheap.

**Lower-cost delegation for quality-tolerant tasks.** #54 centralized model selection and moved several features to a cheaper model. The same logic ran inside the harness: subagents for grep-and-summarize, the main thread for changes that touch verified behavior, lower-cost models for first-pass drafts.

**Briefs as breadcrumbs.** This is the move from my own [intent-driven-exec playbook](https://github.com/bmardock/bmardock/blob/main/playbooks/intent-driven-exec.md), but it landed differently inside the harness. A brief in `docs/briefs/` was a load-bearing artifact only while the work was happening. The day after the PR landed, the brief got a dated note at the top admitting what changed, and the rule went into `CLAUDE.md`. The trail stayed. The blueprint did not.

The methodology underneath was already fine. What Claude Code gave me was a way to run the loop without ceremony around it.

---

## Where I hit walls

Three places the surface ends today.

**Cross-machine handoff is a workaround, not a feature.**
`WORK_LOG.md` does the job, but only because I write it by hand and the model reads it by hand. There is no session-spanning state inside the tool. When I move from the work laptop to the home laptop, the agent on the second machine knows nothing about the agent on the first machine except what I remembered to commit. The state lives in markdown because the surface does not carry it. I would happily trade a third of the polish in the CLI for a real handoff primitive.

**Cross-repo shared context.**
Most of my month was in one repo. The other repo (`bmardock/bmardock`, playbooks and profile) sat in worktrees off the main one because the harness does not have a clean way to hold context for two repos at once. The trail in the playbooks repo is real work that depends on the trail in the app repo, and there is no way to express that link inside the tool. I currently solve it by pasting paths and reading aloud. That is a workaround, not a feature.

**Cowork and Claude Code are still two surfaces.**
I run a two-surface operating system (documented as a playbook in the app repo): Claude Code for engineering, Cowork for chief-of-staff work, founder updates, interview transcription, calendar wrangling. The two surfaces share memory only by reading the same git repo, and only Cowork has the persistent file-based memory. Claude Code can read what Cowork wrote. Cowork can read what Claude Code wrote. Neither one can ask the other what just happened in the other room. The result is that the same fact gets re-derived in both surfaces, and occasionally the two surfaces disagree about live state because one of them is reading a stale commit.

The pattern in all three: the trail compensates for the surface. Where the surface ends, I write a longer markdown file. That keeps shipping working, but it is the kind of friction I would expect to disappear with another quarter of product work on the harness itself. The first month of a tool is the right time to notice these.

I would not say any of this is broken. It is where the surface ends today. The interesting question is which way the surface moves next.

---

## If I were PM

Two near-term unlocks, both grounded in the friction section.

**Cross-subset memory.** The natural next surface is something between `CLAUDE.md` (permanent) and `WORK_LOG.md` (live state). A scoped memory layer the agent maintains across sessions on a per-project basis, written during the work, readable from any machine, addressable from either Claude Code or Cowork. Today I do this by hand: pull, read, write, commit. A first-party version of `docs/agent-memory.md` would close the cross-machine wall and the Cowork-to-Claude-Code wall in the same move. The shape is already implied by the existing file-based memory system in Cowork; the next surface is making it visible to the CLI and writable from inside an agent session without ceremony.

**A trail surface, not a chat surface.** Right now the CLI is conversational by default. Most of the durable value I got this month came from artifacts that survived the conversation: commits, briefs, memory entries, `WORK_LOG.md` updates. The natural next surface is a first-class trail view, scoped per repo, that an agent reads at session start and writes during the work. Think of it as `git log` for context, with the agent as a contributor. The breadcrumbs are already in the repo. The surface that makes them addressable would let the next session start where the last one left off, on either machine, in either tool.

Neither of these is a new idea. Both are versions of moves I am already making outside the tool. The interesting question is whether the tool absorbs them or leaves them to the user. The trail compensates for the surface either way, but the surface absorbing the trail is what would compound.

---

## Closing

The thesis a month of this left me with: Claude Code's edge is not speed. The edge is context. The speed comes for free once the context is right, and disappears the moment the context drifts.

A month of receipts says the same thing. The PRs landed because the briefs were honest, the memory file pointed forward, and the rules in `CLAUDE.md` did not have to be renegotiated. The walls I hit were all walls where the context surface ended.

The trail is what makes any of this checkable at all. That is the point.

---

## Postscript, two months later

Publishing this in July, two things are worth adding.

First, the biggest item on my "if I were PM" list shipped. Claude Code now carries a persistent, per-project memory directory that the agent reads and writes across sessions, which is close to the exact shape I was faking with `docs/agent-memory.md`. I did not have inside information; the need was just that visible from the outside. The workaround files are still there, but the surface absorbed a real piece of the trail, which is the direction I was betting on.

Second, the loop held. The month described here was not a sprint I recovered from; it is roughly how I still work. The rules file kept accumulating, the work log kept handing off between machines, and the app kept shipping. The patterns that looked like coping mechanisms in week two turned out to be the operating system.

---

*How this was assembled: data extraction by Claude Code (git log, repo grep, file reads), synthesis in Cowork against the receipts, then fact-checked by Claude Code before commit. Every PR number, file path, and rule cited here is in the repo on or before 2026-05-12.*
