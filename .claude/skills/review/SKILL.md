---
name: review
description: Do today's Weavewords spaced-repetition reviews in chat — mixed formats (translate, fill the gap, use in a sentence), graded 0–5 and written back so the SR schedule, XP and streak update like in the app. Use for "review my words", "do my reviews".
argument-hint: "[count]"
---

# /review

1. Read `profile.md`. Call `get_due_words` (language = target, limit = count, default 10).
   - `PRO_REQUIRED`: explain that chat reviews need Pro and offer `/quiz` on recent words instead, without saving.
   - Nothing due: congratulate the learner, show `get_stats` (streak, due tomorrow if known) and offer `/story` or a lesson.
2. Rotate formats so it doesn't get repetitive, one word per message:
   - **Recall:** native-language translation → the learner writes the word.
   - **Gap:** an example sentence with the word blanked (use the stored `examples` if present).
   - **Use it:** "Write a sentence with ‹word›." Judge whether the usage is natural.
   - **Meaning:** the word → the learner explains or translates it.
3. Grade each answer on the SM-2 scale and tell the learner briefly:
   - 5 instant and correct;
   - 4 correct after hesitation or a tiny slip;
   - 3 correct with a hint;
   - 2 wrong but close;
   - 1 wrong;
   - 0 no idea.

   Give the correct answer plus one line of help for anything below 4.
4. At the end, call `record_reviews` **once** with every `{itemId, quality}` and `mode` = `"quiz"`. Report the XP, how many were reviewed, and the next dates for the missed words.
5. Log one line to `progress.md` and add words that scored ≤2 to **Weak words**.
