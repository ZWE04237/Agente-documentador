# AGENTS.md

Este repositorio es el espacio de construcción del Agente Documentador nativo para OpenCode.

**Ámbito:** trabaja únicamente dentro de este repositorio (la carpeta que contiene este `AGENTS.md`). No modifiques archivos externos.

Sigue estrictamente: [PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md](PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md)

## Estado actual

- Agente real: `.opencode/agent/documentador.md`
- Comando: `.opencode/commands/documentador.md` (`/documentador`)
- Índice de documentación: `docs/INDEX.md`
- No existe `.tpl.md` en `.opencode/agent/`: OpenCode lo descubriría como un agente adicional.

## Reglas
- Evidencia sobre suposición: verifica con `read`/`glob`/`grep` antes de afirmar.
- Usa herramientas nativas de OpenCode (`read`, `glob`, `grep`, `edit`, `write`, `subagent`, `question`, `skill`).
- Delegar con `subagent` (agent: "explore") si la exploración es masiva (>15 archivos o múltiples directorios).
- No inventes archivos, rutas, APIs, scripts o variables.
- Trabajo exclusivo a este repositorio.
