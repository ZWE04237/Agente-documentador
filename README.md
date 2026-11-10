# Agente Documentador para OpenCode

## Objetivo
Un subagente nativo para OpenCode que explora, mapea y documenta repositorios **basándose únicamente en evidencia**. Genera documentación veraz, accionable y mantenible (`README.md`, `ARCHITECTURE.md`, etc.) sin inventar archivos, rutas, comandos o scripts.

## Requisitos
- OpenCode V2 (compatible con la ruta V1 de agentes).
- Sin dependencias de runtime ni build.
- Git opcional: solo es necesario para generar `CHANGELOG.md`.

## Instalación

### En otro repositorio (recomendado)
1. Copia `.opencode/agent/documentador.md` a tu repositorio en `.opencode/agent/documentador.md`.
2. Copia `.opencode/commands/documentador.md` a `.opencode/commands/documentador.md`.
3. Abre el repositorio en OpenCode. El agente `documentador` y el comando `/documentador` quedan disponibles.

> OpenCode V2 prefiere `.opencode/agents/documentador.md` (plural). También descubre la ruta singular `agent/`; ambas producen el mismo ID.

### Usar este repositorio como fuente
Abre este repositorio en OpenCode y ejecuta `/documentador` directamente. No hace falta copiar nada.

## Uso

Ejecuta el comando con una petición:

```text
/documentador Documenta este repositorio. Genera README.md y ARCHITECTURE.md con evidencia.
/documentador Revisa la documentación actual y sincronízala con el código. Propón solo cambios mínimos.
/documentador Genera un índice navegable en docs/INDEX.md con enlaces verificados.
/documentador Genera un CHANGELOG.md a partir de los commits recientes.
/documentador Ayúdame a entender la arquitectura de este repositorio sin generar archivos nuevos.
```

Sin argumentos, `/documentador` documenta el repositorio completo. También puedes pedirlo en lenguaje natural al agente principal: "Usa el subagente documentador para...".

## Utilidades

| Acción | Resultado |
| :-- | :-- |
| **Documentar completo** | Genera `README.md` y `ARCHITECTURE.md` con punto de entrada, módulos y flujo principal. |
| **Sincronizar docs** | Detecta desincronización entre código y documentación (scripts, rutas rotas, entry points) y propone cambios mínimos. |
| **Crear índice** | Genera `docs/INDEX.md` con enlaces verificados solo si hay >= 2 archivos de documentación. |
| **Crear changelog** | Genera `CHANGELOG.md` basado únicamente en commits de git (omite si no hay historial). |
| **Entender un repo desconocido** | Explora, mapea y sintetiza la arquitectura sin generar documentación innecesaria. |
| **Extras opcionales** | Genera `docs/adr/*.md`, `docs/OPERATIONS.md` o diagramas Mermaid *únicamente* si hay evidencia y añaden valor. |

## Estructura

```text
.opencode/agent/documentador.md      # Subagente (system prompt + permisos)
.opencode/commands/documentador.md   # Comando /documentador
ARCHITECTURE.md                      # Arquitectura de este proyecto
docs/                                # Especificación, guías y reportes
docs/INDEX.md                        # Índice navegable
prompts/                             # Plantillas de prompts por paso
```

Consulta [docs/INDEX.md](docs/INDEX.md) para la documentación completa.

## Notas
- **Evidencia obligatoria** - Todo lo que escribe es verificable con `glob`, `grep` o `read`.
- **Validación estricta** - No entrega sin pasar su checklist y autoevaluación.
- **Git opcional** - Funciona con o sin repositorio git.
- **Solo nativo** - Usa únicamente las herramientas nativas de OpenCode.
- **Mínimo y quirúrgico** - Prioriza corregir sobre reescribir. Si no hay evidencia, lo omite.
- **Autocontenido** - El agente no depende de las guías de este repositorio para funcionar en otro proyecto.

## Licencia

MIT. Consulta [LICENSE](LICENSE).
