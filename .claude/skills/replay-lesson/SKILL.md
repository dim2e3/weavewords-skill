---
name: replay-lesson
description: Run a lesson that already exists in the Weavewords app (generated there or saved from chat) here in chat, then complete it so the app shows it as done. Use for "do my Weavewords lesson", "replay lesson <title>".
argument-hint: "[lesson id or title]"
---

# /replay-lesson

1. Call `list_lessons`. Not available, or `NOT_AVAILABLE`: lessons aren't enabled for this account; offer `/lesson` instead.
   - With no argument: show the 5 most recent lessons that aren't completed (title, language, minutes, from app or chat) and ask which one.
   - With an argument: match it against id or title.
2. Call `get_lesson` and run its content exactly as in `/lesson` step 2 and `method/lesson-method.md`. Use the stored items as they are; don't regenerate them.
3. Finish as in `/lesson` step 3: show the summary, then call `complete_lesson` with this lesson's id and the per-word results.
   - If it reports `alreadyCompleted`, tell the learner the XP was already awarded the first time.
4. Log one line to `progress.md`.
