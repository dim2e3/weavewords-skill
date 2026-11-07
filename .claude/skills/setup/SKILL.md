---
name: setup
description: Create or update the learner profile (profile.md) and check the Weavewords connection and Pro status. Use on first run, when the learner wants to change language/level/goal, or when profile.md is missing.
argument-hint: "[language] [level]"
---

# /setup

1. **Read the current `profile.md`** if it exists.
2. **Check Weavewords.** Call `get_profile`.
   - It works: use `nativeLanguage` and `learningLanguage` as defaults and note `pro`.
   - The tool is missing or says "authentication required": tell the learner to run `/mcp`, choose **weavewords** and press **Authenticate**, then sign in on the Weavewords page that opens and press **Allow**. Continue without it if they want; lessons still work locally.
3. **Ask, one question per message** (skip anything already known or given as arguments):
   - target language. It must be one of the `supportedLanguages` from `get_profile`; Weavewords supports en, de, es, fr, pl, ru, uk;
   - native language, and the language for explanations (default: native);
   - level (A1–C2). If they're unsure, offer a quick 10-question placement check: mix vocabulary, grammar and a short reading, start at A2, and move up or down after every two answers;
   - goal (travel, work, exams, conversation…) and 2–3 interests;
   - preferred lesson length: 10, 15, 30, 45 or 60 minutes (default 15).
4. **Write `profile.md`** in the existing format, including `Save words to Weavewords: yes/no`. Default is yes if `pro` is true; otherwise no, and explain that saving needs Pro.
5. **Summarise in 3 lines** and suggest the next step: `/plan-lessons` if `lessons/<lang>/plan.md` doesn't exist, otherwise `/lesson`.
6. Create `progress.md` with a `# Progress` heading if it doesn't exist.
