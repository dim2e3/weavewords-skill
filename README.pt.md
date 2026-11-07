# Tutor de IA do Weavewords

[English](README.md) · [Deutsch](README.de.md) · [Español](README.es.md) · [Français](README.fr.md) · [Polski](README.pl.md) · [Українською](README.uk.md) · [По-русски](README.ru.md)

Transforme o Claude Code no seu tutor de idiomas pessoal em cerca de 5 minutos. Você não precisa saber programar.

O tutor:
- segue um plano de curso para o seu nível;
- dá **as mesmas lições de 8 seções do app Weavewords** (descoberta, colocações, formação de palavras, detetive de erros, conversação…);
- corrige cada resposta;
- lembra dos seus erros;
- mantém sua conta **Weavewords** sincronizada. Palavras novas vão para o seu dicionário, quizzes e lições no chat atualizam seu cronograma de revisão espaçada, e seu XP e sua sequência aparecem no app.

Funciona para inglês, alemão, espanhol, francês, polonês, russo e ucraniano.

## Início rápido

1. Instale o [Claude Code](https://claude.com/claude-code).
2. Clone o tutor e inicie o Claude:
   ```bash
   git clone https://github.com/dim2e3/weavewords-skill.git
   cd weavewords-skill
   claude
   ```
   Aprove o servidor MCP `weavewords` quando for solicitado.
3. Conecte sua conta: execute `/mcp`, escolha **weavewords** e depois **Authenticate**. A página do Weavewords abre: faça login (ou crie uma conta) e clique em **Allow**.
4. Execute `/setup`, depois `/plan-lessons` e depois `/lesson`.

As lições também funcionam sem conectar. Salvar palavras, revisões no chat e salvar lições na sua conta exigem o **Weavewords Pro**.

## Comandos

| Comando | O que faz |
|---|---|
| `/setup` | Idioma, nível, objetivo; verifica a conexão |
| `/plan-lessons` | Plano de curso para o seu nível |
| `/lesson [n\|tema] [minutos]` | Lição completa de 8 seções com suas palavras pendentes |
| `/save-words` | Salvar palavras no seu dicionário Weavewords |
| `/review` | As revisões de hoje, no chat |
| `/quiz` | Múltipla escolha com suas palavras pendentes |
| `/discover`, `/collocations`, `/word-forms`, `/error-detective` | Exercícios curtos (uma seção da lição cada) |
| `/speak [tema]` | Conversação orientada (texto ou voz) |
| `/story [tema]` | Leitura graduada feita com suas palavras |
| `/write` | Escrita com correções |
| `/mine-words` | Encontrar palavras que valem a pena aprender em qualquer texto |
| `/replay-lesson` | Refazer uma lição salva na sua conta |
| `/daily` | Rotina diária de 10–15 minutos |
| `/progress` | Seu progresso e o que fazer a seguir |

Pedidos comuns também funcionam: *"vamos estudar"*, *"me faça um quiz"*, *"repita a lição 3"*.

## Outros apps de IA

O servidor MCP do Weavewords é `https://api.weavewords.org/mcp` (login via OAuth). As skills são comandos do Claude Code, mas as ferramentas funcionam em qualquer lugar:

- **Claude.ai / Claude Desktop:** Configurações → Conectores → *Adicionar conector personalizado* e cole a URL.
- **ChatGPT:** Configurações → Apps e conectores → Avançado → *Modo desenvolvedor* e crie um conector com a URL (a disponibilidade depende do plano).
- **Codex:** `codex mcp add weavewords --url https://api.weavewords.org/mcp` e depois `codex mcp login weavewords`.
- **Cursor / VS Code:** adicione um servidor MCP HTTP chamado `weavewords` com a URL.

Em apps sem skills, peça ao assistente para ler o `CLAUDE.md` e o `.claude/skills/<nome>/SKILL.md` correspondente, ou cole-os nas instruções do projeto.

## Privacidade

- O `progress.md` e as lições geradas ficam no seu computador (estão no `.gitignore`).
- A conexão recebe apenas as permissões que você aprovar. Desconecte quando quiser em Weavewords → Configurações → **Apps de IA**.
