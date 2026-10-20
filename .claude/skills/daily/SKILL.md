---
name: daily
description: A 10–15 minute daily routine — a few SR reviews, a micro-lesson or short story, and a streak/stats summary. Designed to be run every day (works with /loop or a scheduled task). Use for "daily practice", "my 10 minutes".
---

# /daily

1. Read `profile.md` and `progress.md`. Call `get_stats` and show one motivating line: streak, words due today.
2. **Reviews (≈5 min):** run `/review` with 5 words. Without Pro, a 5-question `/quiz` on recent words instead.
3. **Learn (≈5–7 min):** alternate by day of the week:
   - Mon, Wed, Fri: a **10-minute `/lesson`** (next plan lesson, 10-minute row of the method table);
   - Tue, Thu: `/story`;
   - Sat: `/speak`;
   - Sun: `/write`.

   If `progress.md` shows a recurring mistake, start with 2 `/error-detective` items on it.
4. **Wrap-up:** call `get_stats` again and show XP today and the streak. Name one word to notice in real life today.
5. Log one line to `progress.md`.

Tip for the learner: in Claude Code, `/loop 24h /daily` or a scheduled task will remind you every day.
