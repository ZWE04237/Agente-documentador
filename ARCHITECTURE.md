# Arquitectura

## Propósito

Este repositorio empaqueta un subagente documentador para OpenCode. No contiene código ejecutable ni build: es una definición de agente más una base de conocimiento en Markdown que la respalda.

## Componentes

| Componente | Ruta | Responsabilidad |
|---|---|---|
| Definición del agente | `.opencode/agent/documentador.md` | System prompt, permisos y flujo que ejecuta OpenCode. |
| Comando de invocación | `.opencode/commands/documentador.md` | Expone `/documentador` y selecciona el agente `documentador`. |
| Especificación | `docs/AGENT_SPEC_OPENCODE.md` | Identidad, herramientas, estándares y restricciones. |
| Guías operativas | `docs/*_GUIDE.md`, `docs/*_RULES.md` | Reglas de exploración, mapeo, redacción, sincronización, índice y changelog. |
| Validación | `docs/VALIDATION_CHECKLIST.md` | Criterios obligatorios antes de entregar. |
| Proceso | `PROMPT_MAESTRO_...md`, `ROADMAP_...md`, `prompts/` | Rol, fases y plantillas de trabajo del proyecto. |
| Índice | `docs/INDEX.md` | Navegación verificada de la documentación. |

## Capas

1. **Invocación:** el usuario ejecuta `/documentador` o pide al agente principal que use el subagente `documentador`.
2. **Ejecución:** OpenCode carga `.opencode/agent/documentador.md` en una sesión hija con sus permisos.
3. **Conocimiento:** el agente aplica las reglas descritas en su propio system prompt, que condensan las guías de `docs/`.
4. **Evidencia:** `read`, `glob` y `grep` verifican cada afirmación; `subagent(explore)` solo se usa para descubrimiento masivo.
5. **Entrega:** el agente valida rutas, comandos y enlaces antes de cerrar con `Validado con evidencia`.

## Flujo principal

1. `/documentador <petición>` expande la plantilla de `.opencode/commands/documentador.md` y selecciona el agente.
2. El agente ejecuta INTAKE y define el alcance.
3. Explora el repositorio con `glob`/`grep` y lee archivos concretos con `read`.
4. Identifica punto de entrada, módulos y flujo; sintetiza qué hace frente a cómo está implementado.
5. Redacta `README.md`, `ARCHITECTURE.md` o los documentos solicitados solo con evidencia.
6. Valida rutas, comandos, variables y enlaces.
7. Entrega el resumen con evidencia y la firma `Validado con evidencia`.

## Permisos del agente

- Lectura y descubrimiento: `read`, `glob`, `grep`.
- Escritura de documentación: `edit` (incluye `write`).
- Delegación: solo al subagente `explore`.
- Shell: únicamente lectura de git (`status`, `log`, `show`, `diff`, `branch`).
- Web: bloqueada; la evidencia debe estar en el repositorio.

## Decisiones verificables

- El agente es autocontenido: no depende de las guías de este repositorio para funcionar en otro proyecto.
- No existe plantilla `.tpl.md` en `.opencode/agent/`: OpenCode descubriría ese archivo como un agente adicional. La especificación y las guías cumplen ese papel.
- Los artefactos de prueba (`test-e2e/`, `test-sync/`, `test-docs/`) son temporales y no se conservan; los reportes documentan la evidencia.
- `CHANGELOG.md` no se genera en este repositorio porque no hay historial de git, conforme a `docs/CHANGELOG_GUIDE.md`.

## Evidencia

- Rutas de agente y comando verificadas con `glob`/`read`.
- Reglas y flujo verificados en `.opencode/agent/documentador.md`.
- Estructura verificada en `docs/PROJECT_STRUCTURE.md` y `docs/INDEX.md`.
