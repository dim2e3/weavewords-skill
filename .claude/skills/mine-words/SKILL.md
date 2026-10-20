---
name: mine-words
description: Extract words worth learning from any text the learner pastes (article, lyrics, subtitles, chat, email) — above their level and not already in their Weavewords dictionary — explain them in context and save the chosen ones. Use for "find new words in this text", "what should I learn from this".
argument-hint: "[paste text after the command]"
---

# /mine-words

1. Read `profile.md`. Ask for the text if none was given. Long texts are fine: work through them in chunks.
2. Pick candidates: words and set phrases **at or slightly above** the learner's level that are useful and frequent. Skip names, very rare words and anything basic for their level. Normalise to dictionary forms. Aim for 8–15.
3. Call `check_words` (target language) and drop what they already have. Mention the known words that appear in the text as a quick confidence boost: "you already know: …".
4. Show a numbered table: `word — meaning in context (native language) — the sentence from the text`. Mark the 5 you recommend most with ★.
5. Ask which to keep (numbers, "★" or "all"). Then save through the `/save-words` flow: `add_words` with the original sentence as the example and the tag `From: <short source title>`.
6. Offer a 3-question quick check on the saved words (`/quiz` style) and log one line to `progress.md`.
