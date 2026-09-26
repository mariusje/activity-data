# Decisions

One entry per decision. Newest at the bottom.

## Template

## [Date] — [Short title]
**Decision:** what was decided
**Alternatives considered:** what was rejected
**Rationale:** why
**Status:** current / revised [date]
## 2026-09-26 — Training data as the project domain

**Decision:** The project is built on training data. No further search for
alternative domains.
**Alternatives considered:** A bounded round evaluating other domains against
the goals in PROJECT.md. An earlier, longer ideation round in claude.ai
produced no stronger candidate.
**Rationale:** Measured against the three goals in PROJECT.md: the domain is
neutral for learning AI-assisted development; strong for building something
useful to me, since I am a real user with my own data and a need I can
describe; and strong for interesting work, since I have interest and knowledge
in it. The weakness is that it was not compared with alternatives and differs
little from intervals.icu and Dreeve. That only affects the bonus goal of
something sellable.
**Status:** current

## 2026-09-26 — Platform: web app

**Decision:** The application will be a web app, responsive enough to be
usable from both a desktop browser and a phone browser (Mac and iPhone are
the devices at hand). Not a native mobile app.
**Alternatives considered:** Native mobile app (iOS, given the available
devices). Usage is split roughly evenly between after-session phone checks
and desk-based data exploration, with no clear primary arena; a native app
would force a primary form factor or require building two apps.
**Rationale:** Measured against the three goals in PROJECT.md: (1) learning
AI-assisted development is served better by web's faster edit/preview loop,
with no compile, provisioning, or signing friction, and broader AI tooling
fluency in the stack — relevant since experience with both web and mobile-
native development is close to zero; (2) usefulness to me benefits from one
codebase covering both usage contexts (phone and desk) on the two devices I
actually have; freedom in reporting and maps (PROJECT.md: "freedom wins")
fits a desktop-capable web UI better than a touch-first native UI; (3) no
strong difference for interesting work. Two secondary criteria were also
weighed: web offers the faster learning loop, and it is far easier to hand
to other users later — reachable by URL, no Apple Developer account, no App
Store review, no iPhone-only lock-in.
**Status:** current
