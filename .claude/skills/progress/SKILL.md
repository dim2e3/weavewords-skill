---
name: progress
description: Progress report from progress.md and Weavewords stats — lessons done, words saved and mastered, reviews due, streak, weak topics and recurring mistakes — with a recommended next step. Use for "how am I doing", "my progress".
---

# /progress

1. Read `profile.md`, `progress.md` and `lessons/<lang>/plan.md`.
2. If connected, call `get_stats` (target language). With Pro, also call `list_words` sort=hardest, limit 5.
3. Report in a compact block:
   - **Course:** lessons done out of the plan total, and the last lesson's score.
   - **Words:** total, mastered, in progress, added this week, due today.
   - **Habit:** current streak (longest), XP today and total.
   - **Strengths:** 2 things going well, from scores and progress notes.
   - **Focus next:** the top 3 weak words and the top 2 recurring mistakes.
4. Recommend **one** next action with the exact command: `/review` if more than 10 words are due, else the next `/lesson`, else `/error-detective <point>` for the top recurring mistake.
