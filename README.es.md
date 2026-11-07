# Tutor con IA de Weavewords

[English](README.md) · [Deutsch](README.de.md) · [Français](README.fr.md) · [Polski](README.pl.md) · [Português](README.pt.md) · [Українською](README.uk.md) · [По-русски](README.ru.md)

Convierte Claude Code en tu tutor de idiomas personal en unos 5 minutos. No necesitas saber programar.

El tutor:
- sigue un plan de curso para tu nivel;
- imparte **las mismas lecciones de 8 secciones que la app Weavewords** (descubrimiento, colocaciones, formación de palabras, detective de errores, expresión oral…);
- corrige cada respuesta;
- recuerda tus errores;
- mantiene sincronizada tu cuenta de **Weavewords**. Las palabras nuevas van a tu diccionario, los cuestionarios y las lecciones en el chat actualizan tu calendario de repaso espaciado, y tu XP y tu racha aparecen en la app.

Funciona con inglés, alemán, español, francés, polaco, ruso y ucraniano.

## Inicio rápido

1. Instala [Claude Code](https://claude.com/claude-code).
2. Clona el tutor e inicia Claude:
   ```bash
   git clone https://github.com/dim2e3/weavewords-skill.git
   cd weavewords-skill
   claude
   ```
   Aprueba el servidor MCP `weavewords` cuando te lo pida.
3. Conecta tu cuenta: ejecuta `/mcp`, elige **weavewords** y luego **Authenticate**. Se abre la página de Weavewords: inicia sesión (o crea una cuenta) y pulsa **Allow**.
4. Ejecuta `/setup`, después `/plan-lessons` y después `/lesson`.

Las lecciones también funcionan sin conectar la cuenta. Guardar palabras, los repasos en el chat y guardar lecciones en tu cuenta requieren **Weavewords Pro**.

## Comandos

| Comando | Qué hace |
|---|---|
| `/setup` | Idioma, nivel, objetivo; comprueba la conexión |
| `/plan-lessons` | Plan de curso para tu nivel |
| `/lesson [n\|tema] [minutos]` | Lección completa de 8 secciones con tus palabras pendientes |
| `/save-words` | Guardar palabras en tu diccionario de Weavewords |
| `/review` | Los repasos de hoy, en el chat |
| `/quiz` | Opción múltiple con tus palabras pendientes |
| `/discover`, `/collocations`, `/word-forms`, `/error-detective` | Ejercicios cortos (una sección de la lección cada uno) |
| `/speak [tema]` | Práctica oral guiada (texto o voz) |
| `/story [tema]` | Lectura graduada creada con tus palabras |
| `/write` | Escritura con correcciones |
| `/mine-words` | Encontrar palabras que vale la pena aprender en cualquier texto |
| `/replay-lesson` | Repetir una lección guardada en tu cuenta |
| `/daily` | Rutina diaria de 10–15 minutos |
| `/progress` | Tu progreso y qué hacer a continuación |

También funcionan peticiones normales: *«vamos a estudiar»*, *«hazme un test»*, *«repite la lección 3»*.

## Otras apps de IA

El servidor MCP de Weavewords es `https://api.weavewords.org/mcp` (inicio de sesión con OAuth). Los skills son comandos de Claude Code, pero las herramientas funcionan en cualquier lugar:

- **Claude.ai / Claude Desktop:** Configuración → Conectores → *Añadir conector personalizado* y pega la URL.
- **ChatGPT:** Configuración → Apps y conectores → Avanzado → *Modo desarrollador*, y crea un conector con la URL (la disponibilidad depende del plan).
- **Codex:** `codex mcp add weavewords --url https://api.weavewords.org/mcp` y luego `codex mcp login weavewords`.
- **Cursor / VS Code:** añade un servidor MCP HTTP llamado `weavewords` con la URL.

En apps sin skills, pide al asistente que lea `CLAUDE.md` y el `.claude/skills/<nombre>/SKILL.md` correspondiente, o pégalos en las instrucciones del proyecto.

## Privacidad

- `progress.md` y tus lecciones generadas se quedan en tu ordenador (están en `.gitignore`).
- La conexión solo obtiene los permisos que apruebas. Puedes desconectarla cuando quieras en Weavewords → Configuración → **Apps de IA**.
