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

**A mano:** copia la carpeta `skills/<nombre>/` dentro de `.claude/skills/` de tu proyecto (solo ese proyecto)
o de `~/.claude/skills/` (todos tus proyectos).

## Skills

| Skill | Qué hace |
| --- | --- |
| [`revision-cruzada`](skills/revision-cruzada/SKILL.md) | Cuando Claude termina un trabajo, se lo pasa a GPT (vía OpenCode) para que lo revise sin poder tocar nada, y aplica solo lo que comprueba que es verdad. Vale con Gemini, DeepSeek, Kimi y otros. |

## Licencia

MIT. Úsalas, cámbialas y compártelas.
