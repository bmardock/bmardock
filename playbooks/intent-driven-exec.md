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

Blueprint to breadcrumb. Map to trail. The artifacts are still there. Th
