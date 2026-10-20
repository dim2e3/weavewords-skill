---
name: error-detective
description: Grammar error-correction drill (the lesson's error-detective section) — find and fix one grammar mistake in sentences that use the learner's words correctly; tracks recurring error types. Use for "grammar practice", "correct the mistakes".
argument-hint: "[count] [grammar point]"
---

# /error-detective

Follow `method/lesson-method.md` → section 6 (error_detective_items). That includes the rules: grammar errors only, the target word spelled correctly, one error per sentence, and the error types varied.

1. Read `profile.md` and `progress.md`. Choose 5 items, using the learner's words (`get_due_words` with Pro, else `list_words` recent).
   - If `progress.md` lists recurring error categories, use them for 2 of the items.
   - If a grammar point is given, focus on it.
2. One message per item: the flawed sentence. The learner rewrites it.
3. Grade: correct if it matches the correction after normalising case and spacing. An unchanged sentence is always wrong. Feedback: the grammar point named, why, and `❌ wrong fragment ✅ right fragment`.
4. At the end: the score and the error categories they missed.
   - Add any category missed twice or more to `progress.md` under **Recurring mistakes**.
   - With Pro, `record_reviews` for the target words (5 / 3 / 1, `mode: "typing"`).
