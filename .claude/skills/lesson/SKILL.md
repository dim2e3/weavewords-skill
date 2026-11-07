---
name: lesson
description: Run a full Weavewords 8-section vocabulary lesson in chat (warm-up, discovery, collocations, multiple choice, word formation, error detective, speaking, rapid fire), built around words due for review, then complete it in Weavewords for SR progress and XP. Use for "let's study", "next lesson", "/lesson 3", or a lesson on a topic.
argument-hint: "[lesson number | topic] [10|15|30|45|60]"
---

# /lesson

Follow `method/lesson-method.md` exactly. It defines the sections, the item counts per duration, the chat rules and the scoring.

## 1. Prepare

1. Read `profile.md`, `lessons/<lang>/plan.md` and `progress.md`.
   - With no number or topic: take the first plan lesson not marked done in `progress.md`.
   - With a number: that plan lesson.
   - With a topic: a one-off lesson on it.
   - If there's no plan and no topic, suggest `/plan-lessons` or ask for a topic.
   - If `progress.md` has a lesson marked *started*, offer to resume it from its JSON file.
2. Pick the duration: the argument, else `profile.md`'s lesson length, else 15.
3. Pick the **target words** (the in-app lesson does the same):
   - if Pro, call `get_due_words` (language = target, limit = 6) and include the due words that fit the topic;
   - add the plan's vocabulary for this lesson;
   - add recurring mistakes and weak words from `progress.md`.

   Keep 8–12 in total. Show the list in one line and let the learner add or remove words.
4. Generate the whole lesson in the `save_lesson` shape, with sections sized by the duration table and every target word tested by at least one graded item. Save it to `lessons/<lang>/NNN-<slug>.json`.
5. If Pro, call `save_lesson` and remember the `lessonId`. On `INVALID_LESSON`, fix the field and retry once.
6. Append `- <date> Lesson NNN <topic>: started` to `progress.md`.

## 2. Teach

Go through the sections in order. **One item per message**, and wait for the answer every time.

1. **Warm-up** — ask the question. React naturally and correct only big mistakes. Not scored.
2. **Discovery cards** — gapped sentence and options. After the answer, reveal the pattern and 2–3 examples.
3. **Collocations** — list the candidate phrases; the learner names the natural ones.
4. **Multiple choice** — stem and options, then the explanation and a natural example.
5. **Word formation** — base word and gapped sentence; check against `expected_form` and `acceptable_forms`.
6. **Error detective** — the flawed sentence; the learner rewrites it. Feedback uses `❌ … ✅ …`, and you note the error category.
7. **Speaking** — the situation. Coach the answer: did they use ≥3 target expressions, what are the main corrections, what would a more natural version be.
8. **Rapid fire** — quick prompts, a one-line correction each.

As you go, track `{word, correct, hint_used}` per target word; the last answer wins. If the learner asks for the translation or rule before answering, set `hint_used`. They can say "stop" at any time: keep the results and leave the lesson *started* in `progress.md`.

## 3. Finish

1. Show a summary: score per section, the 3 strongest and 3 weakest words, and one grammar tip.
2. If the lesson was saved and the learner is Pro, call `complete_lesson` with all results. Report `xpEarned` and how many words were reviewed.
   - Results for words not yet in their dictionary don't count. Offer `/save-words` for those, then they'll appear in future reviews.
3. Update `progress.md`: mark the lesson done with its score and list weak words and recurring error categories (these feed future lessons).
4. Suggest the next step: `/save-words` for new words, the next lesson, or `/review` if many words are due.
