---
name: quiz
description: Context multiple-choice quiz (the lesson's MCQ section) on the words due for review in Weavewords, with an explanation and a natural example after each answer; results update the SR schedule. Use for "quiz me", "test me on my words".
argument-hint: "[count]"
---

# /quiz

Follow `method/lesson-method.md` → section 4 (mcq_items).

1. Read `profile.md`. Call `get_due_words` (language = target, limit = count, default 8).
   - Without Pro, or if nothing is due: use `list_words` (recent) and say the results won't update reviews.
2. One question per message: a realistic sentence whose gap tests the word's meaning or usage, plus 4 options (A–D). The distractors are near-synonyms, common learner confusions, or wrong collocations. Never make them obvious.
3. After each answer: ✓/✗, why in one line, and one natural example. If they asked for the translation first, it counts as a hint.
4. At the end, give the score, list the missed words, and call `record_reviews` once with all `{itemId, quality}` (5 clean, 3 hinted, 1 wrong) and `mode: "quiz"`. Report the XP and when the missed words come back.
5. Log one line to `progress.md`.
