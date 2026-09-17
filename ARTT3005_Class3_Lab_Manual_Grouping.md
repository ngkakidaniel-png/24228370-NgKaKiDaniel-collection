# ARTT3005 · Lab Manual — Class 3, Block 2
## The Machine's Grouping

In Block 1 you grouped your own records by hand and wrote a heading for each group.

Now you ask a machine to group the same twenty records. No training, no embeddings, no maths. You hand it your file and you read what it says.

---

## Contents

| | |
|---|---|
| **Part 0** | Before you start |
| **Part 1** | Grouping A — from your words |
| **Part 2** | Grouping B — from your absences |
| **Part 3** | Grouping C — from the pictures |
| **Part 4** | Write them into records.json |
| **Part 5** | See them on the board |
| **Part 6** | Compare |
| **Part 7** | When it breaks |
| **Appendix** | The shape of a grouping |

---

# Part 0 · Before you start

You need three things from Block 1 (`board.html`), all in your `studentID-studentName-collection/` folder:

```
studentID-studentName-collection/
├── board.html
├── records.json          ← the machine will read and then edit this
├── arrangement.json      ← YOUR grouping, from Block 1 (`board.html`)
└── media/
```

> **Do not delete `arrangement.json`.** It holds the grouping you made yourself, and Part 6 has nothing to compare against without it.

---

# Part 1 · Grouping A — from your words

The machine reads the text of your records. It never sees a single picture.

In Cursor, press **⌘ / Ctrl + L** and paste this:

```
Read records.json in this folder.

Group these records into 3 to 6 groups.

Rules:
- Use only the ids that appear in the file. Do not invent, merge or rename any record.
- Every record goes into exactly one group.
- Give each group a heading that argues for why those records belong
  together. Not a category label. "Sounds" is a label. "Things I could
  hear but not photograph" is an argument.
- Then list any record you found hard to place, and say what made it hard.

Reply with JSON only. No explanation before or after it.

{
  "scheme": "words",
  "groups": [ { "heading": "...", "members": ["REC-001", "REC-004"] } ],
  "hard_to_place": [ { "id": "REC-009", "why": "..." } ]
}
```

### **Save that reply.** Put it in a file called `grouping-words.json`.

### Read `hard_to_place` before anything else

That list is the most useful thing on the screen.

In Block 1 you were asked which card you moved a lot. This is the same question, answered by something that has no feelings about your collection. **If it struggled with the same record you struggled with, that record is genuinely difficult, and it is probably interesting.**

---

# Part 2 · Grouping B — from your absences

Same records. One field.

```
Group the same records again, into 3 to 6 groups, but this time use
ONLY the not_captured field. Ignore the title, the date, the place,
the recorder and the file. Ignore what the thing is.

Group them by what was lost, not by what was kept.

Same rules and same JSON shape as before. Set "scheme" to "absence".
```

### Save it as `grouping-absence.json`.

### What to look for

You wrote twenty sentences about what your records failed to hold. Grouped on their own, they answer a question no other view can:

**Do you lose the same thing every time, or a different thing each time?**

If the machine can only make two groups out of your twenty absences, they are nearly all the same absence — and that single, repeating loss is probably the real subject of your work.

If it makes six groups and still finds them hard to place, every encounter lost something different, and there is no one lack to point at.

Both are findings. You should know which one you have.

---

# Part 4 · Write them into records.json

```
I have tw0 grouping files in this folder: grouping-words.json,
grouping-absence.json.

Add a "groupings" object to every record in records.json, like this:

  "groupings": {
    "words": "Things I could hear but not photograph",
    "absence": "Losses that are about temperature"
  }

Use the group heading as the value. If a record is not in a grouping,
set that key to null rather than leaving it out.

Also add my own grouping from arrangement.json under the key "mine".

Do not change any other field. Do not reorder the records.
Show me one finished record before you write the file.
```

> **"Show me one finished record before you write the file"** is the important line. Read it. If the machine has quietly renamed a key or dropped `not_captured`, you catch it now rather than in Part 5.

Every record should now look like this at the bottom:

```json
"not_captured": "The warmth of palms when changing coins",
"certainty": 4,
"groupings": {
  "mine": "Things I could hear but not photograph",
  "words": "The stall as a working machine",
  "absence": "Losses you can only feel with your hands"
}
```

---

# Part 5 · See them on the board

Add a switch to the board you already have.

```
In board.html, add a dropdown to the bottom bar labelled "Grouping".

Fill it from the keys inside the "groupings" object in records.json,
plus a first option called "none".

When a grouping is chosen:
- give every card a coloured outline, one colour per group heading
- cards whose value is null get a thin dashed grey outline instead
- show a legend in the top-left listing each heading with its colour
  and how many records are in it

Do not move any card. Do not change any other behaviour.
```

Now switch between them and watch the same twenty cards change allegiance.

**Leave the cards where you put them in Block 1.** The positions are yours; only the colours change. That is what makes the comparison legible: your arrangement stays still while four different opinions wash over it.

---

# Part 6 · Compare

Switch the dropdown to **mine**, then to **words**, then to **absence**.

Answer these three comparison, question yourself.

**1.** Which two records did *you* put together that no machine grouping keeps together? What were you going on that none of them could read?

**2.** Which grouping came closest to yours — words, absence? Does that tell you something about how you were thinking when you made yours?

**3.** Take the record every grouping found hard to place. Why is it hard? Is it a weak record, or is it the most interesting thing you have?

### Then one line for your board heading

> Write the heading you would give the whole board now, having seen three versions of it.

---

# Part 7 · When something goes wrong

| What you see | What it actually is | Fix |
|---|---|---|
| It invented ids that are not in your file | It was summarising instead of grouping | Say "use only the ids in the file" again, and paste the list of ids |
| It put every record in one group | Your twenty encounters really are similar | That is a finding. Ask for exactly four groups and see what it does |
| The JSON will not parse | It wrapped the reply in explanation | Ask again: "reply with JSON only, nothing before or after" |
| `groupings` overwrote `not_captured` | It rewrote the file rather than editing it | `git restore records.json`, then ask again with "do not change any other field" |
| The dropdown is empty | `groupings` was written at the top of the file, not inside each record | Ask it to put `groupings` inside every record object |


---

# Appendix · The shape of a grouping

A grouping file:

```json
{
  "scheme": "absence",
  "groups": [
    {
      "heading": "Losses you can only feel with your hands",
      "members": ["REC-003", "REC-011", "REC-018"]
    },
    {
      "heading": "Losses that are smells",
      "members": ["REC-001", "REC-007", "REC-012", "REC-016"]
    }
  ],
  "hard_to_place": [
    { "id": "REC-013", "why": "the absence described is social, not physical" }
  ]
}
```

| Field | What it is |
|---|---|
| `scheme` | What the machine was allowed to look at. `words`, `absence`, `pictures`, or `mine`. |
| `groups[].heading` | Its argument for why these belong together. Judge it the way you would judge your own. |
| `groups[].members` | Record ids. Must already exist in your file. |
| `hard_to_place` | Where it hesitated. Read this first. |
