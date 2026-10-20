---
name: plan-lessons
description: Build a course plan (lessons/<lang>/plan.md) for the learner's target language and level — 15–25 lessons, each with one grammar focus and 8–12 words. Use after /setup or when the learner changes language or level.
argument-hint: "[number of lessons]"
---

# /plan-lessons

1. Read `profile.md`. If it's missing, run `/setup` first.
2. If Weavewords is connected (`get_profile` works), call `get_stats` and `list_words` with `sort=recent`, `limit=50` to see what the learner already has.
   - Don't plan words they already know well.
   - Plan to *use* known words inside the lessons rather than teach them again.
3. Draft **15–25 lessons** (default 16) for the profile's level, moving gently toward the next level.
   - Each lesson has a **topic** tied to the goal and interests, **one grammar focus**, and **8–12 words or phrases** that are useful at that level. Prefer collocations and chunks ("make a decision") over isolated words.
   - Order the lessons so grammar builds up and vocabulary is recycled. End with a review lesson for every 5–7 lessons.
4. Show the plan as a table: `# | Topic | Grammar focus | Vocabulary`. Ask whether to change anything.
5. Write it to `lessons/<lang>/plan.md`, using the same format as the sample `lessons/en/plan.md`. If a plan already exists, overwrite it only after the learner confirms.
6. Suggest `/lesson 1`.
