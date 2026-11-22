---
name: save-words
description: Save words and phrases from a lesson or conversation to the learner's Weavewords dictionary (with translations, an example, part of speech, level and the "AI tutor" tag) so they enter spaced-repetition review. Use after a lesson or when the learner says "save these words".
argument-hint: "[words…]"
---

# /save-words

1. **Collect the words**: the arguments if given; otherwise the target words and new phrases from the current lesson or conversation.
2. **Normalise** each one to its dictionary form: infinitive verbs, singular nouns, no articles; keep set phrases and collocations whole ("make a decision"). Remove duplicates.
3. Call `check_words` with the learner's target language. Drop the words that already exist and say which ones ("already in your dictionary: …").
4. **Show the final list and ask for confirmation.** Show each word as `word — translation (native language) — example sentence from the lesson`. Let the learner remove or edit items. **Never save without a yes.**
5. Call `add_words` once:
   - `language` = the target language code;
   - `collectionName` = the plan's course name or "AI Tutor · <Language>" (the server default);
   - `tags` = `["AI tutor"]` always, for every save, whether the words came from a lesson or a conversation. Use this one tag only: never create per-lesson tags such as "Lesson 001: …";
   - `words` = `[{word, translation: [1–3 translations in the native language], examples: [the sentence from the lesson], explanation: a short usage note, partOfSpeech, level, usageType}]`.
   - Always fill the three classification fields, so the word shows them in the app:
     - `partOfSpeech`: `noun`, `verb`, `adjective`, `adverb`, `preposition`, `pronoun`, `conjunction`, `interjection` or `article`. Leave it out for set phrases and collocations.
     - `level`: the word's CEFR level (A1–C2). If unsure, use the learner's level from `profile.md`.
     - `usageType`: `formal`, `informal`, `slang`, `literary`, `academic` or `technical`. Leave it out for neutral words.
   - Show these three next to each word in step 4, so the learner can correct them before saving.
6. Report: N saved, M already there, and any failures with their reasons. Mention that the words now appear in Weavewords reviews (web and Android) after sync.
7. Append to `progress.md`: `  - saved to Weavewords: N words, tag "AI tutor"`.

Errors:
- `PRO_REQUIRED`: print the list as a table they can copy, mention the `upgradeUrl` once, and continue.
- `QUOTA_EXCEEDED`: say when it resets and keep the list in `progress.md` under "to save".
- The tool is unavailable or unauthenticated: explain `/mcp` → weavewords → Authenticate, then print the list.
