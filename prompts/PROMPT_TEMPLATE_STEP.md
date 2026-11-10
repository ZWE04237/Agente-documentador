# PROMPT TEMPLATE STEP - AGENTE DOCUMENTADOR OPENCODE

## ID/Paso
- **Fase:** [XX]
- **Paso:** [XX.Y]
- **Nombre:** [Nombre descriptivo del paso]
- **Prioridad:** [CRÍTICA | ALTA | MEDIA | BAJA]
- **Tiempo estimado:** [X-Y min]

## Objetivo
[Descripción clara de qué se quiere lograr con este paso]

## Contexto
- **Referencia obligatoria:** [PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md](../PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md)
- **Ruta de trabajo:** `este repositorio`
- **Filosofía:** Explorar -> Mapear -> Comprender -> Sintetizar -> Documentar | Evidencia sobre suposición

## Herramientas OpenCode a usar
- [ ] `read` - Lectura de archivos/carpetas
- [ ] `glob` - Descubrimiento por patrón
- [ ] `grep` - Búsqueda de símbolos/config
- [ ] `edit` - Cambios quirúrgicos
- [ ] `write` - Creación/reemplazo controlado
- [ ] `subagent` (agent: "explore") - Delegación si masivo (>15 archivos / múltiples dirs)
- [ ] `question` - Solo si ambigüedad real bloquea
- [ ] `skill` - Solo si aplica

## Tareas (checklist)
- [ ] [Tarea 1]
- [ ] [Tarea 2]
- [ ] [Tarea 3]

## Entregables
- [ ] [Archivo/carpeta 1]
- [ ] [Archivo/carpeta 2]

## Criterios de aceptación
- [ ] Trabaja ÚNICAMENTE en `este repositorio`
- [ ] Todo lo afirmado está respaldado por evidencia (archivos leídos)
- [ ] Sin inventar rutas/archivos/APIs/scripts/variables
- [ ] Comandos/rutas mencionados verificados
- [ ] Coherente con el PROMPT_MAESTRO
- [ ] Mínimo viable y accionable

## Riesgos/Mitigación
| Riesgo | Mitigación |
|---|---|
| [Riesgo 1] | [Mitigación 1] |
| [Riesgo 2] | [Mitigación 2] |

## Validación cruzada
- [ ] Revisado con `read` tras crear/editar
- [ ] Verificado con `glob`/`grep` si hay referencias
- [ ] Sin enlaces rotos internos
- [ ] Sin referencias fuera del ámbito

## Prompt listo para pegar
```text
# PROMPT: FASE [XX] - PASO [XX.Y] | [NOMBRE]

Actúa como Big Pickle siguiendo estrictamente PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md.

RUTA DE TRABAJO: este repositorio

OBJETIVO:
[Objetivo conciso]

TAREAS:
[Lista numerada con acciones concretas usando herramientas OpenCode]

REGLAS:
- Trabaja ÚNICAMENTE en este repositorio
- Evidencia sobre suposición
- Usa herramientas nativas
- Delegar con subagent(explore) si masivo
- No inventar nada

VALIDAR: [Qué debe verificarse antes de entregar]
ENTREGABLE: [Lo que se debe entregar]
```
