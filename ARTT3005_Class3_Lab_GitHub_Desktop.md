# ARTT3005 · Lab Manual
## Undoing things, with GitHub Desktop

You are letting an AI rewrite your files. At some point it will take something that worked and break it.

This is the page you open when that happens. No terminal. No commands. Five buttons.

> **Read the table first, use the right one.** Most of the damage in this course comes from people picking the wrong undo and making things worse.

---

## Which one do I need?

| What happened | What to use | Where |
|---|---|---|
| I edited files and have **not committed**. I want them back the way they were. | **Discard changes** | Changes tab |
| I **committed** but have **not pushed**, and the commit was a mistake. | **Undo** | Changes tab |
| I **already pushed** and need to take it back. | **Revert Changes in Commit** | History tab |

The line that matters is **have you pushed yet**. Before pushing, the history is yours to rewrite. After pushing, it belongs to everyone who has a copy — so you add a new commit that reverses the old one instead of pretending it never happened.

---

# 1 · Discard changes

*You edited files. You have not committed. You want the last committed version back.*

**One file:**

1. Go to the **Changes** tab in the left sidebar.
2. **Right-click the file** in the list.
3. Click **Discard changes…**
4. Confirm.

**Everything you have changed:**

1. In the menu bar, go to **Branch → Discard all changes…**
2. Confirm.

> ⚠️ **This one is not undoable from inside the app.** There is no history for work that was never committed, so there is nothing to go back to. GitHub Desktop moves the discarded files to the Trash / Recycle Bin, so look there first if you panic — but do not rely on it.
>
> **The lesson is upstream of the button: commit before you let the AI touch a file that works.**

---

# 2 · Undo

*You committed. You have not pushed. The commit was wrong.*

1. Go to the **Changes** tab.
2. Directly under the commit box you will see **Undo** with the message of your last commit next to it.
3. Click it.

The commit disappears from history, and **all the changes come back into your working directory** as uncommitted edits. Nothing is lost. You can now fix them and commit again, or discard them.

> Only the **most recent** commit, and only if it has **not been pushed**.
>
> If you just want to fix the commit *message*, or add one more file to that same commit, use **Amend commit** instead — History tab, right-click the top commit.


---

# 3 · Revert Changes in Commit

*You already pushed. The commit has to go.*

1. Go to the **History** tab.
2. **Right-click the commit → Revert Changes in Commit**

This does not delete anything. It makes a **new commit** that undoes exactly what the old one did. Both commits stay in your history, which is the honest record of what happened: you did a thing, then you undid it.

Then **Push origin** as usual.

> Reverting several commits? Go **newest first**. Out of order and you will hit merge conflicts.


---

# The habit that prevents all of this

| | |
|---|---|
| **Commit when something works** | Not when you have finished. When it *works*. That is your save point. |
| **Write what you did** | `added pins to the map` beats `update`. In three weeks, `update` tells you nothing. |
| **Commit before you let the AI loose** | One commit takes ten seconds. Rebuilding an afternoon takes an afternoon. |
| **Push at the end of every session** | Work that only exists on your laptop does not exist. |
