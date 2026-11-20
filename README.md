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
| [`explicar-en-web`](skills/explicar-en-web/SKILL.md) | Convierte lo que sea en una web visual que se abre en tu navegador: te explica lo que no entiendes con dibujos y un ejemplo que puedes tocar, te pone varias opciones lado a lado para que elijas, te monta un prototipo con controles para ajustar valores o te deja ordenar una lista en columnas. Lo que eliges vuelve solo a Claude Code (o lo copias y lo pegas en cualquier otro agente). Ajusta la sección "Mi estilo" y te la hará a tu gusto a la primera. |

## Licencia

MIT. Úsalas, cámbialas y compártelas.
