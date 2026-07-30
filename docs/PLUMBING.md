# The plumbing layer

Every screen carries a switch marked **Show the plumbing**. It is the same interaction on all
nine, borrowed from the course studio, where it was built first.

**Off.** The page reads in ordinary English. No IDs, no field names, no types, no jargon.

**On.** Nothing moves. What changes:

- every label crossfades in place to its real field name, set in Geist Mono, with a type chip
- a reserved provenance strip fills in under the numbers it belongs to
- a panel opens from the right listing, for every figure on screen, the table or event behind
  it, whether it is computed live, on write, or on a schedule, and whether it exists in
  Origna8 today or has to be built
- the panel footer states the total cost and compares it against the other directions

The strips reserve their height whether or not they are filled, so turning the switch on never
reflows the page. That is the point: Andrew and Jawad are looking at the same screen.

## Where the switch is

| Screen | Placement |
|---|---|
| `andrew-authoring.html` | in the page header, right of the stats |
| `learner-a-competitive.html`, `learner-b-mastery.html` | in the page header, right of the stats |
| `v1` through `v5` | in the demo bar at the bottom |

The five archived directions keep it in the demo bar deliberately. They have five different
bespoke headers, and forcing a control into each one would have meant redesigning work whose
whole purpose is to be compared as it was.

## What the counts mean

Two tables are needed by any version of Educa8 and are never counted as a difference between
directions:

| Table | What it holds |
|---|---|
| `chapter_completion` | user_id, chapter_id, read_at |
| `retrieval_check_attempt` | user_id, chapter_id, correct, attempt_index, answered_at, next_due_at |

Everything above that floor is what the direction costs. The price list on the hub is drawn
from these panels.

| Screen | New tables | Events | Jobs | The line that carries the cost |
|---|---|---|---|---|
| 03 The publication | 3 | 2 | 0 | Nothing. No streak, no board, no sessions. |
| B Relevance and mastery | 5 | 1 | 1 | The concept taxonomy and the loan-attribute rules. Authoring work. |
| 02 The syllabus | 6 | 3 | 2 | "Minutes read" needs a session heartbeat. |
| 01 The dashboard | 7 | 3 | 2 | The sparkline and the competency readout. |
| A Competition, and 05 | 7 | 3 | 2 | Streak rollover per timezone, and a rank fast enough to feel live. |
| 04 The instrument | 8 | 4 | 2 | The run log. One write every thirty seconds per active reader. |

## Two costs that are easy to underestimate

**The streak has to roll over at midnight in each officer's own timezone.** Pacific Ridge is
one branch, but the moment there are two, a single nightly job at one hour is wrong for
somebody, and a streak that breaks unfairly is worse than no streak.

**Any "minutes read" figure needs a heartbeat, not a timer.** A tab left open overnight must
not count as nine hours of study, which means an event stream plus a rule for when an idle
session stops counting. Directions 02 and 04 both depend on this. Direction 04 depends on it
heavily.

## The one cost that is not engineering

Variant B needs a concept taxonomy, roughly forty entries, and a rule set mapping loan
attributes (`product_type`, `purpose`, `occupancy`, income type, lock state) to those concepts.
That is content work and it belongs to Andrew, in the studio, not to Jawad. It is the reason B
is cheap in infrastructure and still not free.

## Implementation note

The layer is namespaced `pl-*` throughout, in both the CSS and the markup, so it cannot collide
with a page's own class names. It was unprefixed at first and silently broke direction 04,
whose own `.ph` and `.lb` classes were overwritten by the injected ones.
