# Weavewords KI-Tutor

[English](README.md) · [Español](README.es.md) · [Français](README.fr.md) · [Polski](README.pl.md) · [Português](README.pt.md) · [Українською](README.uk.md) · [По-русски](README.ru.md)

Damit wird Claude Code in etwa 5 Minuten zu deinem persönlichen Sprachtutor. Programmierkenntnisse brauchst du nicht.

Der Tutor:
- folgt einem Kursplan für dein Niveau;
- führt **dieselben 8-teiligen Lektionen wie die Weavewords-App** durch (Entdecken, Kollokationen, Wortbildung, Fehlerdetektiv, Sprechen…);
- prüft jede Antwort;
- merkt sich deine Fehler;
- hält dein **Weavewords**-Konto synchron. Neue Wörter landen in deinem Wörterbuch, Quizze und Lektionen im Chat aktualisieren deinen Wiederholungsplan, und XP und deine Serie erscheinen in der App.

Funktioniert für Englisch, Deutsch, Spanisch, Französisch, Polnisch, Russisch und Ukrainisch.

## Schnellstart

1. Installiere [Claude Code](https://claude.com/claude-code).
2. Klone den Tutor und starte Claude:
   ```bash
   git clone https://github.com/dim2e3/weavewords-skill.git
   cd weavewords-skill
   claude
   ```
   Bestätige den MCP-Server `weavewords`, wenn du gefragt wirst.
3. Verbinde dein Konto: Führe `/mcp` aus, wähle **weavewords** und dann **Authenticate**. Die Weavewords-Seite öffnet sich: Melde dich an (oder erstelle ein Konto) und klicke auf **Allow**.
4. Führe `/setup` aus, dann `/plan-lessons`, dann `/lesson`.

Lektionen funktionieren auch ohne Verbindung. Wörter speichern, Wiederholungen im Chat und das Speichern von Lektionen in deinem Konto erfordern **Weavewords Pro**.

## Befehle

| Befehl | Was er macht |
|---|---|
| `/setup` | Sprache, Niveau, Ziel; prüft die Verbindung |
| `/plan-lessons` | Kursplan für dein Niveau |
| `/lesson [n\|Thema] [Minuten]` | Vollständige 8-teilige Lektion mit deinen fälligen Wörtern |
| `/save-words` | Wörter in deinem Weavewords-Wörterbuch speichern |
| `/review` | Die heutigen Wiederholungen, im Chat |
| `/quiz` | Multiple Choice mit deinen fälligen Wörtern |
| `/discover`, `/collocations`, `/word-forms`, `/error-detective` | Kurze Übungen (je ein Lektionsteil) |
| `/speak [Thema]` | Sprechtraining mit Coaching (Text oder Stimme) |
| `/story [Thema]` | Lesetext auf deinem Niveau, aus deinen Wörtern |
| `/write` | Schreiben mit Korrekturen |
| `/mine-words` | Lernenswerte Wörter in einem beliebigen Text finden |
| `/replay-lesson` | Eine in deinem Konto gespeicherte Lektion wiederholen |
| `/daily` | Tägliche Routine von 10–15 Minuten |
| `/progress` | Dein Fortschritt und was als Nächstes kommt |

Einfache Bitten funktionieren auch: *„lass uns lernen“*, *„frag mich ab“*, *„wiederhole Lektion 3“*.

## Andere KI-Apps

Der Weavewords-MCP-Server ist `https://api.weavewords.org/mcp` (Anmeldung per OAuth). Die Skills sind Befehle für Claude Code, die Tools funktionieren aber überall:

- **Claude.ai / Claude Desktop:** Einstellungen → Konnektoren → *Benutzerdefinierten Konnektor hinzufügen*, dann die URL einfügen.
- **ChatGPT:** Einstellungen → Apps & Konnektoren → Erweitert → *Entwicklermodus*, dann einen Konnektor mit der URL erstellen (je nach Abo verfügbar).
- **Codex:** `codex mcp add weavewords --url https://api.weavewords.org/mcp`, dann `codex mcp login weavewords`.
- **Cursor / VS Code:** einen HTTP-MCP-Server namens `weavewords` mit der URL hinzufügen.

In Apps ohne Skills bitte den Assistenten, `CLAUDE.md` und die passende `.claude/skills/<name>/SKILL.md` zu lesen, oder füge sie in die Projektanweisungen ein.

## Datenschutz

- `progress.md` und deine erstellten Lektionen bleiben auf deinem Computer (sie sind in `.gitignore`).
- Die Verbindung erhält nur die Berechtigungen, die du bestätigst. Du kannst sie jederzeit unter Weavewords → Einstellungen → **KI-Apps** trennen.
