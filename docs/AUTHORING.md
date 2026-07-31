# Andrew's side · the authoring view

## Who this is for

**Andrew is not technical.** He is the person who writes and uploads the course content.
He does not know what a slug is, does not want to see an ID, and should never meet the
word "schema." If he opens this screen and feels like he needs a developer, the design
has failed.

**Jawad is technical.** He is going to build the backend from this. He needs to see the
objects, the fields, the types, and what talks to what.

Both people open the same screen. One switch decides which one it is speaking to.

## The switch

Put it in the page header, right side, clearly labelled. Off by default.

```
Show the plumbing   ( ●───  )
```

**Off, plain.** Everything reads in ordinary English. Labels are what a person would say
out loud. No IDs, no field names, no types, no JSON, no jargon anywhere on screen.

**On, technical.** The same screen, same layout, nothing moves. What changes:

- Every field label swaps to its real field name, set in Geist Mono
- A small type chip appears beside each one: `text` `int` `enum` `uuid` `bool` `richtext`
- Real IDs and slugs appear under the things they belong to
- A right-hand panel slides in showing the live JSON of the object being edited, updating
  as you type
- Relationship lines get named: `chapter.course_id → course.id`
- The publish action shows what it actually fires

The transition should be one deliberate animation, not a page reload, and not a fade on
everything at once. Labels crossfading in place while the JSON panel slides in reads as
one system revealing its insides, which is the point.

## The wording map · use exactly these pairs

| Plain (Andrew) | Technical (Jawad) | Type |
|---|---|---|
| Course | `course` | `uuid` |
| Lesson | `chapter` | `uuid` |
| Subject | `category` | `enum` |
| Who it is for | `level` | `enum` beginner / intermediate / advanced |
| Short description | `summary` | `text` |
| How long it takes | `duration_minutes` | `int` |
| The writing | `body` | `richtext` |
| Order | `order_index` | `int` |
| Must finish first | `requires[]` | `uuid[]` |
| Question at the end | `retrieval_check` | `object` |
| The answer | `correct_index` | `int` |
| Why that is the answer | `explanation` | `text` |
| What they earn | `xp_award` | `int` |
| Bonus for the question | `check_xp` | `int` |
| Worth less after a week | `decay_after_days` | `int` |
| Who can see this | `visibility` | `enum` draft / published / branch |
| Goes to the scoreboard | `posts xp_event → domina8_standings` | `event` |
| Saved but not live | `status: draft` | `enum` |
| Live | `status: published` | `enum` |
| Cover colour | `category_color` | `hex` |

Never show both at once. That is the whole trick.

## What the screen has to do

A full course builder, in the order Andrew would actually work:

1. **All courses.** A list with status, who can see each one, how many lessons, when it
   was last touched, and how many people are partway through. Draft and live are visually
   distinct at a glance. This is the landing state.
2. **Make a course.** Name, subject, who it is for, short description, cover colour picked
   from the six real category colours.
3. **Add lessons and put them in order.** Drag-to-reorder, or up and down controls that
   actually work in the demo. Say plainly what happens to learners partway through when
   the order changes.
4. **Write a lesson.** A real writing surface with the chapter-one copy in it. Simple
   formatting only: headings, bold, lists, a definition block. Word count and a live read
   of how long it takes, so "how long it takes" is measured rather than guessed.
5. **Add the question at the end.** Write a prompt, three or four answers, mark the right
   one, write why. Andrew should be able to do this without being told what retrieval
   practice is.
6. **Set what must be finished first.** Pick from the other courses. Show what it opens
   and what it blocks, in a sentence, not a graph.
7. **Set what they earn**, with the effect stated in plain terms: "finishing this lesson
   moves someone about one place on their branch board."
8. **Preview as a learner.** Show the actual reader view of what he just wrote, inline,
   so he can see it the way an LO will. This is the single most reassuring control on the
   page for a non-technical person and it should be prominent.
9. **Publish**, with a clear statement of who will see it and when.

Make at least the lesson editor, the question builder, and the plumbing toggle genuinely
interactive. Typing in the editor should update the word count and the estimate. Marking
a correct answer should show. The JSON panel in technical mode must reflect real typed
input.

## State to show

Andrew is mid-flight, not starting from zero. Six courses exist. Five are live. One,
**Rate Lock Strategies**, is a draft he is partway through, with three lessons written and
the fourth empty. Open on that, because a half-finished thing shows far more of the system
than an empty form does.

## Voice, in plain mode

Short. Ordinary. The way you would explain it to a colleague. "This lesson is live. 14
people have started it." Not "chapter published, 14 active enrollments." Never a tooltip
that explains a term the design should not have used.
