# Korepetytor AI Weavewords

[English](README.md) · [Deutsch](README.de.md) · [Español](README.es.md) · [Français](README.fr.md) · [Português](README.pt.md) · [Українською](README.uk.md) · [По-русски](README.ru.md)

W około 5 minut zamienisz Claude Code w swojego osobistego korepetytora językowego. Nie musisz umieć programować.

Korepetytor:
- prowadzi cię według planu kursu dla twojego poziomu;
- prowadzi **te same 8-częściowe lekcje co aplikacja Weavewords** (odkrywanie, kolokacje, słowotwórstwo, detektyw błędów, mówienie…);
- sprawdza każdą odpowiedź;
- pamięta twoje błędy;
- synchronizuje twoje konto **Weavewords**. Nowe słowa trafiają do twojego słownika, quizy i lekcje na czacie aktualizują twój harmonogram powtórek, a XP i seria dni pojawiają się w aplikacji.

Działa dla angielskiego, niemieckiego, hiszpańskiego, francuskiego, polskiego, rosyjskiego i ukraińskiego.

## Szybki start

1. Zainstaluj [Claude Code](https://claude.com/claude-code).
2. Sklonuj korepetytora i uruchom Claude:
   ```bash
   git clone https://github.com/dim2e3/weavewords-skill.git
   cd weavewords-skill
   claude
   ```
   Zatwierdź serwer MCP `weavewords`, gdy pojawi się pytanie.
3. Połącz konto: uruchom `/mcp`, wybierz **weavewords**, a potem **Authenticate**. Otworzy się strona Weavewords: zaloguj się (lub załóż konto) i kliknij **Allow**.
4. Uruchom `/setup`, potem `/plan-lessons`, potem `/lesson`.

Lekcje działają też bez połączenia. Zapisywanie słów, powtórki na czacie i zapisywanie lekcji na koncie wymagają **Weavewords Pro**.

## Polecenia

| Polecenie | Co robi |
|---|---|
| `/setup` | Język, poziom, cel; sprawdza połączenie |
| `/plan-lessons` | Plan kursu dla twojego poziomu |
| `/lesson [n\|temat] [minuty]` | Pełna 8-częściowa lekcja wokół słów do powtórki |
| `/save-words` | Zapisanie słów w słowniku Weavewords |
| `/review` | Dzisiejsze powtórki, na czacie |
| `/quiz` | Test wielokrotnego wyboru ze słów do powtórki |
| `/discover`, `/collocations`, `/word-forms`, `/error-detective` | Krótkie ćwiczenia (każde to jedna część lekcji) |
| `/speak [temat]` | Ćwiczenie mówienia z korektą (tekst lub głos) |
| `/story [temat]` | Tekst do czytania na twoim poziomie, z twoich słów |
| `/write` | Pisanie z poprawkami |
| `/mine-words` | Wyszukiwanie słów wartych nauki w dowolnym tekście |
| `/replay-lesson` | Powtórzenie lekcji zapisanej na koncie |
| `/daily` | Codzienna rutyna na 10–15 minut |
| `/progress` | Twoje postępy i co dalej |

Zwykłe prośby też działają: *„pouczmy się”*, *„przepytaj mnie”*, *„powtórz lekcję 3”*.

## Inne aplikacje AI

Serwer MCP Weavewords to `https://api.weavewords.org/mcp` (logowanie przez OAuth). Skille to polecenia Claude Code, ale narzędzia działają wszędzie:

- **Claude.ai / Claude Desktop:** Ustawienia → Łączniki → *Dodaj własny łącznik*, a potem wklej adres URL.
- **ChatGPT:** Ustawienia → Aplikacje i łączniki → Zaawansowane → *Tryb dewelopera*, a potem utwórz łącznik z adresem URL (dostępność zależy od planu).
- **Codex:** `codex mcp add weavewords --url https://api.weavewords.org/mcp`, a potem `codex mcp login weavewords`.
- **Cursor / VS Code:** dodaj serwer HTTP MCP o nazwie `weavewords` z tym adresem URL.

W aplikacjach bez skilli poproś asystenta o przeczytanie `CLAUDE.md` i odpowiedniego `.claude/skills/<nazwa>/SKILL.md` albo wklej je do instrukcji projektu.

## Prywatność

- `progress.md` i wygenerowane lekcje zostają na twoim komputerze (są w `.gitignore`).
- Połączenie dostaje tylko te uprawnienia, które zatwierdzisz. Możesz je w każdej chwili odłączyć w Weavewords → Ustawienia → **Aplikacje AI**.
