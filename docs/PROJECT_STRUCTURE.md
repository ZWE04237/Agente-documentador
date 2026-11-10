# Estructura del proyecto

| Carpeta/Archivo | Propósito |
|---|---|
| `.opencode/agent/documentador.md` | Subagente real: frontmatter, permisos y system prompt autocontenido. |
| `.opencode/commands/documentador.md` | Comando `/documentador` que invoca al agente. |
| `docs/` | Documentación del propio agente (especificación, guías, reportes). |
| `docs/INDEX.md` | Índice navegable con enlaces verificados. |
| `prompts/` | Plantillas y prompts específicos reutilizables. |
| `ARCHITECTURE.md` | Componentes, capas y flujo del proyecto. |
| `PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md` | Prompt maestro con rol, principios, flujo y estándares. |
| `ROADMAP_AGENTE_DOCUMENTADOR_OPENCODE_BIGPICKLE.md` | Roadmap con fases, pasos y prompts específicos. |
| `README.md` | Visión general, instalación y utilidades. |
| `AGENTS.md` | Instrucciones para agentes que trabajen aquí. |
| `LICENSE` | Licencia MIT. |

## Notas

- No hay código ejecutable ni dependencias: el producto es la definición del agente y su base de conocimiento.
- No existe `assets/`; se creará solo si algún día hace falta almacenar diagramas o capturas.
- No existe `documentador.tpl.md`: OpenCode registraría ese archivo como un agente adicional. La especificación y las guías hacen de plantilla.
- Los artefactos de prueba (`test-e2e/`, `test-sync/`, `test-docs/`) son temporales y se eliminan al cerrar cada prueba; los reportes en `docs/` documentan la evidencia.
- `CHANGELOG.md` se omite porque el repositorio no tiene historial de git, conforme a `docs/CHANGELOG_GUIDE.md`.
