# Skills de Dru

Skills para Claude Code (y cualquier agente compatible: Codex, OpenCode, Cursor...) que uso en mi día a día.
Cada una vive en `skills/<nombre>/SKILL.md` y se instala por separado: coges solo la que quieras.

Las explico en mi canal: **Dru | IA & Tech** (@soydruia en YouTube, TikTok e Instagram).

## Instalar una skill

**La forma fácil:** díselo a tu agente.

> Instala la skill `revision-cruzada` de github.com/DruMoDev/skills en este proyecto.

**Con un comando** (necesita Node.js):

```bash
npx skills add DruMoDev/skills --skill revision-cruzada
```

**En Claude (web o app):** descarga la carpeta `skills/<nombre>/` como zip y súbela en Personalizar > Skills.

**A mano:** copia la carpeta `skills/<nombre>/` dentro de `.claude/skills/` de tu proyecto (solo ese proyecto)
o de `~/.claude/skills/` (todos tus proyectos).

## Skills

| Skill | Qué hace |
| --- | --- |
| [`revision-cruzada`](skills/revision-cruzada/SKILL.md) | Cuando Claude termina un trabajo, se lo pasa a GPT (con Codex) para que lo revise sin poder tocar nada, y aplica solo lo que comprueba que es verdad. Vale con cualquier combinación: Gemini, DeepSeek, Kimi y otros vía OpenCode. |
| [`explicar-en-web`](skills/explicar-en-web/SKILL.md) | Cuando no entiendes algo (un concepto, unas finanzas, un contrato, un código o una conversación entera), te lo convierte en una sola web visual con un ejemplo que puedes tocar: cambias un número y ves qué pasa. Funciona en Claude, ChatGPT y en agentes como Claude Code o Codex. Ajusta la sección "Mi estilo" y te la hará a tu gusto a la primera. |

## Licencia

MIT. Úsalas, cámbialas y compártelas.
