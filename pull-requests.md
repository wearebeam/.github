# Pull request descriptions

Every PR description, hand-written or agent-written, is a short title, a one-sentence What, a one-sentence Why and the ticket link when there is one, so a reviewer absorbs it in under 30 seconds; bug fixes and UI changes add the sections below.

## Format

```markdown
#### What
One plain sentence on what changed.

#### Why
One plain sentence on why it matters.

[TEAM-123](https://linear.app/beamazing/issue/TEAM-123)
```

- End with the linked Linear ticket, when there is one.
- The org "PR description" check fails a description over 40 lines or 500 words, not counting images or comments. If it needs more, split the PR.

## Title

- 2–4 words, as a sentence-case imperative: `Add Order#failure_reason`, `Allow short names`.
- The title is the plain imperative, with no `feat:` or `fix:` prefix; the ticket ID lives in the closing link. Code names are fine.

## What and Why

- What says what changed, subject first, in the present tense. When the old behaviour matters, end with "instead of X".
- Why gives the cost or the reason, with a real number when you have one.
- One sentence is the default. Use bullets for 2–3 separate changes or reasons. Split the PR past 3.
- Keep each sentence or bullet under about 15 words.
- Say what the change causes, not which functions, constants or files it touches; the diff shows those. Naming one key class or flag for orientation is fine.

## Optional sections

These go between Why and the ticket, in this order, each under its own `####` heading.

### Steps to reproduce

Bug fixes add numbered, minimal steps ending with a "Before: X. After: Y." line. The root cause goes in Why.

```markdown
#### Steps to reproduce
1. Open a profile with no optional fields set.
2. Click "Edit".
3. Before: the page crashes with a blank screen. After: the page opens with empty fields.
```

### Screenshots or video

- Anything a user sees gets a screenshot, or a short video for interactions and multi-step flows.
- Drag the file into the GitHub description editor, which hosts it.
- Show several screens in a GitHub table. New feature: one row of screens. Change: Before and After columns, one row per screen.
- Name the state each image shows. Standalone image: a bold caption, `**After: empty attributes shown as placeholders**`. Table: put the state in the column header.

### Diagram

One Mermaid diagram of this change only, when a diagram shows it faster than a sentence. Use a flowchart for how the parts connect, a sequence diagram for a step-by-step exchange, or another Mermaid type that fits. GitHub renders it from a fenced `mermaid` block.

### Review notes

Up to 2 bullets, each pointing the reviewer at something that needs their attention. A note that describes the change belongs in What. This is the one place a label opens a bullet, so the reviewer can sort them:

- `How <thing> works:` one mechanism the reviewer must understand, such as retry timing.
- `Proof:` a check outside CI, with a link.
- `Where to look:` a file and what to check there.
- `Not in scope:` something left out on purpose, such as `Not in scope: the filter on the list page, tracked in TEAM-124.`

## Stacked PRs

One quoted line at the top, before What, gives the position and where the context lives:

```markdown
> 2/3, stacked on #123 — context in #100.
```

The first PR of the stack tells the story; later PRs link to it.

## Excluded content

- No AI attribution, co-author trailers or tool footers.
- No test-plan checklists. CI is the evidence.
- No PR history or changes of direction during development. Describe the code as it is now.
- State a tradeoff only when it departs from the original requirements.

## Example

```markdown
#### What
Reports use only the sources that have data.

#### Why
One empty source failed the whole report.

[TEAM-456](https://linear.app/beamazing/issue/TEAM-456)
```

## Counter-examples

- The five-fact sentence: a 70-word sentence written to avoid bullets. Use one bullet per fact.
- The paragraph: prose under What or Why. Use one sentence, or one bullet per idea.
- The inventory: a bullet per code change ("Add `Foo::Bar.baz`", "Wire it into `Some::Service`", "Add specs"). Say what the change causes; the diff shows the rest.
- The agent default: `## Summary`, `## Changes` and `## Test plan` with checkboxes. Rewrite it as What and Why.
- The bold-label bullet: `**Open the settings page:** a warning banner says…`. Write the plain sentence.
