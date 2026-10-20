---
name: word-forms
description: Word-formation drill (the lesson's word-formation section) — turn a base word into the form that fits the sentence (noun→adjective, verb→noun, adverb, plural, comparative, past…), then optionally save the word family. Use for "word forms", "word families", derivation practice.
argument-hint: "[words…]"
---

# /word-forms

Follow `method/lesson-method.md` → section 5 (word_formation_items).

1. Read `profile.md`. Choose 5 words:
   - the arguments;
   - else `get_due_words` (Pro);
   - else weak words from `progress.md`.

   **Skip words with no real derived forms** and say so.
2. One item per message: a sentence with one gap and the base word in capitals, for example "She answered very ___ (CARE)." The base word must need a real change.
3. Check the answer case-insensitively against the expected form and any acceptable alternatives. Then give the form and the rule in one line, plus 2–3 other members of the word family.
4. At the end: with Pro and dictionary words, `record_reviews` (5 / 3 / 1, `mode: "typing"`). Offer `/save-words` for useful family members the learner doesn't have yet (check them with `check_words` first).
5. Log one line to `progress.md`.
