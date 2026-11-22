---
name: setup
description: Create or update the learner profile (profile.md) and check the Weavewords connection and Pro status. Use on first run, when the learner wants to change language/level/goal, or when profile.md is missing.
argument-hint: "[language] [level]"
---

# /setup

1. **Read the current `profile.md`** if it exists.
2. **Check Weavewords.** Call `get_profile`.
   - It works: note `pro` and prefill the profile from the learner's Weavewords onboarding:
     - `learningLanguage` → **Target language**; `nativeLanguage` → **Native language** and **Explanation language**;
     - `targetLevel` (a1–c2, upper-case it) → **Level**;
     - `learningGoal` → **Goal** and **Interests**: `travel` → goal "travel", interests "travel, culture"; `career` → "work and career", interests "work, career"; `family` → "family and heritage", interests "family, heritage"; `hobby` → "hobbies", interests "hobbies"; `exam` → "exam preparation", interests "exams, study"; `other` or empty → nothing, ask.
     - Older API versions don't return `targetLevel` / `learningGoal`: then only the languages are prefilled.
   - The tool is missing or says "authentication required": tell the learner to run `/mcp`, choose **weavewords** and press **Authenticate**, then sign in on the Weavewords page that opens and press **Allow**. Continue without it if they want; lessons still work locally.
3. **Show what was prefilled** in one message ("From your Weavewords onboarding: English, native Russian, C1, goal travel") and ask only whether to change it. Then **ask, one question per message** about whatever is still missing, or that the learner wants to change (skip anything already known or given as arguments). Interests are always worth one question: the onboarding goal is only a starting guess, so offer the prefilled interests and ask for 1–2 more:
   - target language. It must be one of the `supportedLanguages` from `get_profile`; Weavewords supports en, de, es, fr, pl, ru, uk;
   - native language, and the language for explanations (default: native);
   - level (A1–C2). If they're unsure, offer a quick 10-question placement check: mix vocabulary, grammar and a short reading, start at A2, and move up or down after every two answers;
   - goal (travel, work, exams, conversation…) and 2–3 interests;
   - preferred lesson length: 10, 15, 30, 45 or 60 minutes (default 15).
4. **Write `profile.md`** in the existing format, including `Save words to Weavewords: yes/no`. Default is yes if `pro` is true; otherwise no, and explain that saving needs Pro.
5. **Summarise in 3 lines** and suggest the next step: `/plan-lessons` if `lessons/<lang>/plan.md` doesn't exist, otherwise `/lesson`.
6. Create `progress.md` with a `# Progress` heading if it doesn't exist.
