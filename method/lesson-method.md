# Weavewords lesson method

This is the method the Weavewords app uses to generate its 8-section vocabulary lessons, adapted for running a lesson live in chat. Every lesson skill (`/lesson`, `/discover`, `/collocations`, `/quiz`, `/word-forms`, `/error-detective`, `/speak`, `/replay-lesson`) follows it, so a lesson made here can be saved to your Weavewords account and replayed later with `/replay-lesson`.

## Goal

The learner already recognises the target words. The lesson teaches what makes them sound native: **collocations, word patterns, phrasal combinations and word families**. It is not a vocabulary test.

Progression across the lesson: **SEE IT → NOTICE IT → UNDERSTAND IT → PRACTISE IT → DISTINGUISH IT → USE IT → SPEAK WITH IT.**

## Chat rules (always)

- **One item per message.** Post an item, wait for the answer, give feedback, then post the next item.
- **Never reveal the answer before the learner tries.** Don't put the rule, the correct option or the translation in the same message as the question.
- **Discovery before rules.** Show the gapped sentence and options first. The rule and examples come only after the learner answers.
- **Feedback is short:** right or wrong in one line, then why in one or two lines, using the explanation language from `profile.md`.
  - After two mistakes on the same pattern, give one similar extra item before moving on.
- **Hints count.** If the learner asks for a translation, a hint or the rule before answering, mark that word `hint_used: true`. A correct answer with a hint is not a clean answer.
- Calibrate contexts, sentences and distractors to the learner's CEFR level (`profile.md`), even when the target words themselves are simple. Situations should be realistic and a little challenging, never like a beginner quiz.
- Distractors must be plausible: near-synonyms, common learner errors, or structurally similar patterns. Never obvious filler.
- **Recycle** the same target words across sections 2–6. Don't introduce a word once and drop it.

## Duration → items per section

Use the same item counts as the app. Pick the row for the requested duration; the default is 15 minutes in chat.

| Minutes | warm_up | discovery_cards | collocation_discovery | mcq_items | word_formation_items | error_detective_items | speaking_situations | rapid_fire_prompts |
|---|---|---|---|---|---|---|---|---|
| 10 | 2 | 2 | 2 | 3 | 2 | 2 | 1 | 2 |
| 15 | 3 | 3 | 3 | 4 | 3 | 3 | 1 | 2 |
| 30 | 4 | 5 | 5 | 6 | 5 | 5 | 2 | 3 |
| 45 | 5 | 7 | 7 | 9 | 8 | 8 | 4 | 4 |
| 60 | 6 | 9 | 10 | 12 | 10 | 10 | 5 | 5 |

`save_lesson` rejects sections larger than the row for the declared `durationMinutes`.

## The 8 sections

Field names match `save_lesson`'s `content` and the app's lesson format.

1. **warm_up** — `{question, vocab_hints[]}`. A discussion question about the topic that invites the target words. Not graded.
2. **discovery_cards** — `{sentence_with_blank, options[2-6], correct_option_index, pattern_explanation, examples[]}`.
   - The sentence has **exactly one** blank (one run of underscores, nothing after the closing punctuation).
   - The learner picks an option. Only after that do you reveal `pattern_explanation` and 2–3 complete example sentences. The examples are written correctly, with no blanks.
   - Graded: the word is `options[correct_option_index]`.
3. **collocation_discovery** — `{head_word, candidates[{phrase, is_natural}], explanation}`.
   - Show 4–6 candidate phrases; the learner says which sound natural.
   - Correct only if they choose all the natural ones and none of the unnatural ones.
   - Graded word: `head_word`.
4. **mcq_items** — `{stem, options[2-6], correct_option_index, explanation, natural_example}`. A context multiple choice. After the answer, give the explanation and one natural example. Graded word: the correct option.
5. **word_formation_items** — `{sentence_with_blank, base_word, expected_form, acceptable_forms[], explanation}`.
   - The learner turns `base_word` into the form that fits the gap.
   - `base_word` must **need a real change of form**: noun→adjective, verb→noun, adjective→adverb, plural, comparative, past and so on. Never use a word that already fits as it is. If a target word has no derived forms, test it in another section.
   - Check answers case-insensitively against `expected_form` and `acceptable_forms`. Graded word: `base_word`.
6. **error_detective_items** — `{flawed_sentence, expected_corrections[], error_explanation}`.
   - The error is **grammatical**, in a sentence that uses the target word correctly. The target word is spelled correctly in both versions. Never misspell it, invent a form or swap in a look-alike.
   - `expected_corrections[0]` is the same sentence with only the error fixed.
   - Vary the error type across items:
     - present simple third-person -s;
     - past simple vs present perfect with a finished-time word;
     - present perfect plus for/since;
     - infinitive vs gerund vs wrong verb form;
     - conditionals;
     - comparative or superlative and adjective vs adverb;
     - preposition, article, singular/plural.
   - `error_explanation` names the grammar point, says why it's wrong, and shows `❌ wrong fragment ✅ right fragment`.
   - Graded: correct if the learner's sentence matches a correction after normalising case and punctuation. Submitting the sentence unchanged is always wrong.
7. **speaking_situations** — `{situation, useful_language[]}`.
   - A real-life situation; the learner answers in 3–5 sentences by text or voice.
   - In the app this is ungraded; in chat you **coach** it:
     - check that they used at least 3 target expressions;
     - correct the main errors;
     - offer a more natural version.
   - Reveal `useful_language` only if they ask.
8. **rapid_fire_prompts** — `{prompt}`. Quick questions to answer in one sentence each, using a target expression. Coach briefly.

`target_vocabulary[]` lists every word or phrase the lesson practises, and every one of them must be the tested answer of at least one graded item (sections 2–6).

## Scoring (same as the app)

Keep one result per distinct target word: `{word, correct, hint_used}`. The **last** answer for a word wins.

| Result | SM-2 quality |
|---|---|
| wrong | 1 |
| correct with a hint | 3 |
| correct without help | 5 |

- `complete_lesson` applies exactly this mapping and awards XP once per lesson: 2 × quality per word, +20 for finishing, +30 if every answer was correct.
- Drill skills that don't save a lesson send the same qualities through `record_reviews`. They use `itemId`s from `check_words` / `get_due_words`.
- Words that aren't in the user's dictionary yet can't be reviewed. Offer `/save-words` for them first.

## Saving a lesson

Before starting, write the lesson you generated to `lessons/<lang>/NNN-<slug>.json` in the `save_lesson` input shape. Then, if the user has Pro, call `save_lesson`. This means:
- an interrupted lesson can be resumed from the file;
- the lesson appears in the Weavewords app (Lessons) and can be replayed there.

If `save_lesson` returns `INVALID_LESSON`, fix the field it names and retry once. If it still fails, run the lesson from the file anyway.
