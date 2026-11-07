---
name: replay-lesson
description: Run a lesson saved to the learner's Weavewords account (by /lesson or another chat) here in chat, then complete it so its results count for SR progress and XP. Use for "do my Weavewords lesson", "replay lesson <title>".
argument-hint: "[lesson id or title]"
---

# /replay-lesson

1. Call `list_lessons`. No saved lessons (or the tool isn't connected): offer `/lesson` instead.
   - With no argument: show the 5 most recent lessons that aren't completed (title, language, minutes) and ask which one.
   - With an argument: match it against id or title.
2. Call `get_lesson` and run its content exactly as in `/lesson` step 2 and `method/lesson-method.md`. Use the stored items as they are; don't regenerate them.
3. Finish as in `/lesson` step 3: show the summary, then call `complete_lesson` with this lesson's id and the per-word results.
   - If it reports `alreadyCompleted`, tell the learner the XP was already awarded the first time.
4. Log one line to `progress.md`.
