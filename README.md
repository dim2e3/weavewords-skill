# Weavewords AI Tutor Skill

[Українською](README.uk.md) · [По-русски](README.ru.md)

This turns Claude Code into a personal language tutor in about 5 minutes. You don't need to code.

The tutor:
- follows a course plan for your level;
- runs **the same 8-section lessons as the Weavewords app** (discovery, collocations, word formation, error detective, speaking…);
- checks every answer;
- remembers your mistakes;
- keeps your **Weavewords** account in sync. New words go into your dictionary, chat quizzes update your spaced-repetition schedule, and lessons and XP show up in the app.

Works for English, German, Spanish, French, Polish, Russian and Ukrainian.

## Quick start

1. Install [Claude Code](https://claude.com/claude-code).
2. Clone the tutor and start Claude:
   ```bash
   git clone https://github.com/weavewords/weavewords-tutor.git
   cd weavewords-tutor
   claude
   ```
   Approve the `weavewords` MCP server when asked.
3. Connect your account: run `/mcp`, choose **weavewords**, then **Authenticate**. The Weavewords page opens: sign in (or create an account) and press **Allow**.
4. Run `/setup`, then `/plan-lessons`, then `/lesson`.

Lessons work without connecting too. Saving words, chat reviews and saving lessons to the app need **Weavewords Pro**.

## Commands

| Command | What it does |
|---|---|
| `/setup` | Language, level, goal; checks the connection |
| `/plan-lessons` | Course plan for your level |
| `/lesson [n\|topic] [minutes]` | Full 8-section lesson around your due words |
| `/save-words` | Save words to your Weavewords dictionary |
| `/review` | Today's spaced-repetition reviews, in chat |
| `/quiz` | Multiple choice on your due words |
| `/discover`, `/collocations`, `/word-forms`, `/error-detective` | Short drills (one lesson section each) |
| `/speak [topic]` | Coached speaking (text or voice) |
| `/story [topic]` | Graded reading built from your words |
| `/write` | Writing with corrections |
| `/mine-words` | Find words worth learning in any text |
| `/replay-lesson` | Run a lesson from the Weavewords app here |
| `/daily` | 10–15 minute daily routine |
| `/progress` | Your progress and what to do next |

Plain requests work too: *"let's study"*, *"quiz me"*, *"repeat lesson 3"*.

## Other AI apps

The Weavewords MCP server is `https://api.weavewords.org/mcp` (OAuth sign-in). The skills are Claude Code commands, but the tools work anywhere:

- **Claude.ai / Claude Desktop:** Settings → Connectors → *Add custom connector*, then paste the URL.
- **ChatGPT:** Settings → Apps & Connectors → Advanced → *Developer mode*, then create a connector with the URL (plan availability varies).
- **Codex:** `codex mcp add weavewords --url https://api.weavewords.org/mcp`, then `codex mcp login weavewords`.
- **Cursor / VS Code:** add an HTTP MCP server named `weavewords` with the URL.

In apps without skills, ask the assistant to read `CLAUDE.md` and the relevant `.claude/skills/<name>/SKILL.md`, or paste them into the project instructions.

## Privacy

- `progress.md` and your generated lessons stay on your computer (they're git-ignored).
- The connection only gets the permissions you approve. Disconnect it anytime in Weavewords → Settings → **AI apps**.
