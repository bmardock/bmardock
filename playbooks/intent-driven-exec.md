# Intent-Driven Execution (v3)

## How to work when execution is cheap and direction is expensive

---

AI removed a major bottleneck in how we build.

You can now generate working code in minutes and try multiple approaches in the time it used to take to plan one. Getting something into a usable state is no longer the expensive part.

But removing that constraint didn't make teams uniformly faster. It exposed a different bottleneck.

Not in building.

In deciding what to build and staying aligned as it evolves.

The bottleneck didn't disappear. It moved.

You can see it in how work actually plays out.

Something gets built quickly. It looks right. The team moves forward.

Then later, it becomes clear the direction needs to change.

At that point, the work slows down.

Not because building is hard, but because adjusting direction is.

You can move fast and still end up far from where you need to be.

The question is why that keeps happening.

---

## What actually broke

Two things that used to be load-bearing now are not. Both are easy to miss because both used to be the rational way to work.

### The ceremonies stopped scaling

Sprint planning. PRDs. Design reviews. Stand-ups. Architecture review boards. Alignment meetings before alignment meetings.

These weren't bureaucratic mistakes. They were a rational response to a real cost. When a feature took a quarter to build, the cost of building the wrong one was a quarter. So you spent two weeks aligning, scoping, reviewing, and getting sign-off before you started, because the alternative was worse.

The ceremonies were the scaffolding that made being wrong survivable.

That cost dropped. Building the wrong feature now costs an afternoon. Reverting it costs less.

The scaffolding didn't drop with it.

A team that still runs the full ceremony stack pays the same overhead it always did, against an execution cost that is one fortieth of what it was. The ceremonies aren't producing more alignment. They are producing the same alignment, against a backdrop where the alignment is already stale by the time the meeting ends, because someone else's branch shipped during the planning session.

Teams in this state report feeling productive. The calendar is full. The artifacts are getting produced. The slow part isn't visible from inside the ceremony, because the ceremony is what you'd point to as the proof you're being thorough.

The proof of thoroughness is now the bottleneck.

### The artifacts inverted

The second thing that broke is the role of documentation.

Documentation used to be the blueprint. It was generated before execution, handed off, and used to coordinate. The PRD told engineering what to build. The design doc told reviewers what to evaluate. The artifact preceded the work and constrained it.

That worked when the artifact and the work were both expensive. You couldn't afford for them to diverge, and you couldn't afford to redo either, so you front-loaded the alignment into the artifact and treated it as the contract.

The artifact now diverges from the work the moment the work starts. You build something, you see how it behaves, you change direction, you build again. The PRD that described the original plan is misaligned within hours. By the time it gets a "v2," the code has been through six revisions. Whoever still reads the PRD reads stale information.

The right move is to flip the artifact relationship. Documentation becomes the breadcrumb instead of the blueprint. It is produced during the work, not before it: bugs noticed in use, field notes from real sessions, briefs that get amended after they meet reality, commits that quote the observation they came from, agent-memory files that point forward to where the trail is going next.

Blueprint to breadcrumb. Map to trail. The artifacts are still there. They are produced by the work instead of preceding it.

The repo becomes the institutional memory. A new person joining six weeks in reads the trail and reconstructs the why. An executive reading the trail sees what changed, when, in response to what signal. The trail is more honest than any planning artifact because every entry is anchored to something that happened.

One byproduct worth naming. The documentation produced by the work stays current. The chronic stale-docs problem comes from docs written once, upfront, and frozen while the work moves on. Wikis nobody trusts. READMEs that lie. Notion graveyards. Breadcrumbs don't have that problem because they aren't separate from the work. They are its exhaust. When the work shifts, the trail shifts with it. The condition is that the team actually captures the breadcrumbs as they go. Commit messages that say why. PR descriptions that quote the moment. Field notes that point forward. You don't get evergreen docs by accident. You get them by working in a mode that produces them as a side effect.

The next reader of the trail might not be a person. The agent-memory file isn't named accidentally. When the work includes agents, the trail has to be readable by them too. Blueprint docs assumed a stable team that read them before the work. Breadcrumbs work for whoever shows up next, person or agent. Not a separate paradigm. The same one, extended.

---

## How this looks in real work

A recent stretch on a small recovery app I work on landed two PRs that show the pattern at two scales.

The first started with my cofounder mentioning over breakfast that his check-in from last night still showed up the next morning. By lunch the PR was merged. The fix turned out to be two things: a timezone column that silently defaulted to UTC for any user whose row was written before timezone wiring landed, and a UI state-patch that updated one piece of payload but not the related card. The commit message quotes the original observation verbatim. Three follow-up commits in the same PR close loopholes the first fix exposed. The lesson landed forward in an agent-memory file, ending with a rule for the next person who touches timezone code: "Don't add new tz-aware endpoints without also wiring the heal call." That rule is the breadcrumb. It is the kind of context that, in a ceremony-heavy team, would have been an Architecture Decision Record nobody opens.

The second ran the same loop at feature scale. A brief proposed a new daily practice and explicitly gated the build behind a one-week paper prototype. We built the real thing in a session instead, because scaffolding the real surface (schema, server, frontend, route, verify, commit) cost less than seven mornings of running the paper test, and the paper instrument was the worse test anyway. The brief now carries a dated update at the top of the implementation section that points forward to a "Next step" paragraph explaining why the gate was retired. The lesson moved into the project's standing instructions for every future agent: "When build cost equals test cost, build the real thing."

Two PRs, one week, both running the same move. The thinking happened in the room with the work, was captured during the work, and now lives in the repo as institutional memory the next person reads on their way in.

One thing about the second example is worth naming directly. The brief kept the original "post-dogfood, not before" gate language visible. A reader following the trail sees the original belief, the date it was retired, and the reasoning, in that order. Not a cleaned-up brief. A breadcrumb that shows the bumps.

That is the bar. If your "updated" doc doesn't preserve what it superseded, you don't have a breadcrumb. You have revisionism.

---

## What runs inside the room

The methodology underneath all of this was already fine. Lean and agile teams have been running a version of it for two decades:

**Discovery → Intent → Iterate → Validate → Decide**

The labels aren't the point. They just make the shape easier to see.

What changed is where the loop runs.

It used to run between ceremonies. You did some discovery, you held a planning meeting, you wrote a doc, you ran a review, you scoped the work, you held a kickoff, you executed, you held a demo, you held a retro. The loop existed inside a scaffolding of artifacts and meetings that took longer to traverse than the loop itself. The methodology was fine. The container around it was the bottleneck.

Now the loop runs inside the room with the team and the work. Discovery is open the app, see what is broken or slow, name what should be different. Intent is one sentence about what you are trying to improve. Iterate is the change itself, made directly, often in minutes. Validate is run the new version and watch what happens. Decide is one of three states: keep going, adjust, step back.

Each pass updates both the understanding of the problem and the shape of the solution at the same time.

The docs are exhaust, not prerequisite. Commit messages, briefs amended in place, dated update notes, agent-memory entries. The artifacts are produced as the work moves, and they accumulate into the trail.

This is what allows direction to stay aligned while the work moves forward. The loop is fast because the scaffolding around it isn't slowing it down. The artifacts are useful because they describe what actually happened.

---

## How to run the loop

Each step is simple. The value comes from how they connect.

**Discovery** is understanding the current state and where it falls short.

Sometimes that means running what already exists and noticing where it is confusing, slow, or harder to use than it should be. Other times, like a new feature, it means walking through the expected flow and identifying where uncertainty or friction is likely to show up.

**Intent** is defining what you are trying to improve.

Not a full solution. A direction specific enough that you can tell whether the change worked.

**Iterate** is making a change in that direction.

The goal isn't completeness. It is to create something real that you can evaluate.

**Validate** is running that change and seeing what actually happens.

You are not checking if it matches what was planned. You are checking if it improved the outcome you care about.

In practice, this comes down to a few simple signals:

- Did the user complete the action?
- Was it easier or faster?
- Where did they hesitate or get confused?

**Decide** is choosing what to do next based on that result.

Three options:

- Keep going. It improved things. Continue.
- Adjust. Partial improvement or new friction. Refine.
- Step back. The direction is off. Return to discovery.

Then run the loop again.

The work produced along the way is the trail. Capture it as the change happens, not afterward. The commit message is part of the artifact. The brief amendment is part of the artifact. The dated update note that admits what you used to think is part of the artifact.

## [Run a Pilot](https://github.com/bmardock/bmardock/blob/main/playbooks/Intent-Driven-Execution-Pilot.md)

---

## What changes now

If you read this far and your reaction is "we already do all this," three checks.

Check how many of your alignment artifacts are produced before the work versus during it. If the ratio is heavy on the before side, the artifacts are still functioning as blueprints, not breadcrumbs.

Check the calendar. If the ceremony stack still consumes the same share of the week it did three years ago, the scaffolding is operating at its old cost against an execution cost that has dropped by an order of magnitude. The methodology underneath is fine. The container around it is the bottleneck.

Check what happens to an old plan when the direction changes. If retiring a gate or revising a brief requires a meeting, the artifact is still in charge. If the artifact gets a dated update note that preserves what it used to say, and the work moves on, the trail is in charge.

AI made execution fast. The methodology was already fine. The scaffolding around it wasn't.

The teams that benefit from the new speed are the ones whose ceremonies are smaller, whose artifacts are produced by the work, and whose trails are honest about what changed and when.

The goal isn't to define the right solution upfront.

It is to move toward the right outcome, capture the trail as you go, and let the artifacts describe the work instead of constraining it.
