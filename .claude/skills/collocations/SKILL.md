---
name: collocations
description: Collocation drill for a word (the lesson's collocation-discovery section) — the learner picks which phrases sound natural, then learns the natural ones and can save them. Use for "what goes with <word>", "collocations for <word>".
argument-hint: "<word> [more words…]"
---

# /collocations

Follow `method/lesson-method.md` → section 3 (collocation_discovery).

1. Read `profile.md`. If no word is given, take 3 words from `get_due_words` (Pro) or `progress.md`.
2. For each head word, post 5–6 candidate phrases numbered 1–6: 2–4 natural, the rest plausible but unnatural. Typical traps are wrong verb+noun pairs and calques from the learner's native language. Ask: "Which sound natural?"
3. After the answer: mark each candidate ✓/✗, explain the 1–2 trickiest in one line each, and give one example sentence per natural collocation.
4. Scoring: correct only if the learner chose all the natural candidates and none of the unnatural ones. At the end, with Pro and the head word in the dictionary (`check_words`), call `record_reviews` (quality 5 / 3 / 1).
5. Offer to save the natural collocations as new entries via `/save-words`, for example "make a decision", tagged `Collocations`.
6. Log one line to `progress.md`.
