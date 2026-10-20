---
name: discover
description: Short "discover the pattern" drill (the lesson's discovery-cards section) — gapped sentences with close options, the rule revealed only after answering. Use for quick pattern practice on given words or words due for review.
argument-hint: "[words…] [count]"
---

# /discover

Follow `method/lesson-method.md` → section 2 (discovery_cards) and the chat rules.

1. Read `profile.md`. Choose the words:
   - the arguments if given;
   - else, with Pro, `get_due_words` (limit 5);
   - else weak words from `progress.md`.

   Use 5 items unless a count is given.
2. For each word, one message: a level-appropriate sentence with **exactly one** blank and 2–3 close options (lettered A/B/C). Wait for the answer.
3. Feedback: right or wrong, then the pattern in 1–2 sentences and 2 complete example sentences. Mark `hint_used` if they asked for help first.
4. At the end, show the score. If the words are in their dictionary (`check_words` gives `itemId`s) and they're Pro, call `record_reviews` with quality 5 / 3 / 1 (clean / hinted / wrong) and `mode: "fill_blank"`.
5. Log one line to `progress.md`.
