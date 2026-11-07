# Tuteur IA Weavewords

[English](README.md) · [Deutsch](README.de.md) · [Español](README.es.md) · [Polski](README.pl.md) · [Português](README.pt.md) · [Українською](README.uk.md) · [По-русски](README.ru.md)

Transformez Claude Code en tuteur de langues personnel en 5 minutes environ. Aucune compétence en programmation n'est nécessaire.

Le tuteur :
- suit un plan de cours adapté à votre niveau ;
- propose **les mêmes leçons en 8 sections que l'app Weavewords** (découverte, collocations, formation des mots, détective d'erreurs, expression orale…) ;
- corrige chaque réponse ;
- se souvient de vos erreurs ;
- synchronise votre compte **Weavewords**. Les nouveaux mots vont dans votre dictionnaire, les quiz et les leçons dans le chat mettent à jour votre planning de révision espacée, et vos XP et votre série s'affichent dans l'app.

Fonctionne pour l'anglais, l'allemand, l'espagnol, le français, le polonais, le russe et l'ukrainien.

## Démarrage rapide

1. Installez [Claude Code](https://claude.com/claude-code).
2. Clonez le tuteur et lancez Claude :
   ```bash
   git clone https://github.com/dim2e3/weavewords-skill.git
   cd weavewords-skill
   claude
   ```
   Approuvez le serveur MCP `weavewords` quand on vous le demande.
3. Connectez votre compte : lancez `/mcp`, choisissez **weavewords**, puis **Authenticate**. La page Weavewords s'ouvre : connectez-vous (ou créez un compte) et cliquez sur **Allow**.
4. Lancez `/setup`, puis `/plan-lessons`, puis `/lesson`.

Les leçons fonctionnent aussi sans connexion. Enregistrer des mots, faire des révisions dans le chat et enregistrer des leçons dans votre compte nécessitent **Weavewords Pro**.

## Commandes

| Commande | Ce qu'elle fait |
|---|---|
| `/setup` | Langue, niveau, objectif ; vérifie la connexion |
| `/plan-lessons` | Plan de cours pour votre niveau |
| `/lesson [n\|sujet] [minutes]` | Leçon complète en 8 sections autour de vos mots à réviser |
| `/save-words` | Enregistrer des mots dans votre dictionnaire Weavewords |
| `/review` | Les révisions du jour, dans le chat |
| `/quiz` | QCM sur vos mots à réviser |
| `/discover`, `/collocations`, `/word-forms`, `/error-detective` | Exercices courts (une section de leçon chacun) |
| `/speak [sujet]` | Expression orale accompagnée (texte ou voix) |
| `/story [sujet]` | Lecture graduée construite avec vos mots |
| `/write` | Écriture avec corrections |
| `/mine-words` | Trouver les mots à apprendre dans n'importe quel texte |
| `/replay-lesson` | Refaire une leçon enregistrée dans votre compte |
| `/daily` | Routine quotidienne de 10 à 15 minutes |
| `/progress` | Votre progression et la suite |

Les demandes en langage courant fonctionnent aussi : *« on étudie »*, *« interroge-moi »*, *« refais la leçon 3 »*.

## Autres apps d'IA

Le serveur MCP de Weavewords est `https://api.weavewords.org/mcp` (connexion OAuth). Les skills sont des commandes Claude Code, mais les outils fonctionnent partout :

- **Claude.ai / Claude Desktop :** Paramètres → Connecteurs → *Ajouter un connecteur personnalisé*, puis collez l'URL.
- **ChatGPT :** Paramètres → Apps et connecteurs → Avancé → *Mode développeur*, puis créez un connecteur avec l'URL (disponibilité selon l'abonnement).
- **Codex :** `codex mcp add weavewords --url https://api.weavewords.org/mcp`, puis `codex mcp login weavewords`.
- **Cursor / VS Code :** ajoutez un serveur MCP HTTP nommé `weavewords` avec l'URL.

Dans les apps sans skills, demandez à l'assistant de lire `CLAUDE.md` et le `.claude/skills/<nom>/SKILL.md` concerné, ou collez-les dans les instructions du projet.

## Confidentialité

- `progress.md` et vos leçons générées restent sur votre ordinateur (ils sont dans `.gitignore`).
- La connexion n'obtient que les autorisations que vous approuvez. Déconnectez-la à tout moment dans Weavewords → Paramètres → **Apps d’IA**.
