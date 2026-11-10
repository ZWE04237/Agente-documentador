# Guía: generación del subagente documentador

## Propósito

Esta guía explica cómo generar y mantener el subagente real `.opencode/agent/documentador.md` a partir de la especificación y las guías del repositorio.

## Cuándo usarlo

Tras cambiar `docs/AGENT_SPEC_OPENCODE.md` o cualquiera de las guías de `docs/`, regenera el agente para que su system prompt refleje las reglas vigentes.

## Pasos

1. Revisar `docs/AGENT_SPEC_OPENCODE.md` y las guías afectadas (`EXPLORATION_RULES.md`, `ARCHITECTURE_MAPPING_GUIDE.md`, `WRITING_RULES.md`, `DIAGRAMS_ADR_GUIDE.md`, `DOC_SYNC_GUIDE.md`, `INDEX_GUIDE.md`, `CHANGELOG_GUIDE.md`, `VALIDATION_CHECKLIST.md`).
2. Crear o actualizar `.opencode/agent/documentador.md` con frontmatter V2 válido:
   ```yaml
   ---
   description: ...
   mode: subagent
   permissions: [...]
   ---
   ```
3. Escribir el cuerpo como system prompt autocontenido: identidad, principios, herramientas, flujo de 7 pasos, reglas y autoevaluación. No enlaces a las guías internas, porque el agente debe funcionar en cualquier repositorio.
4. Verificar que el agente no imponga rutas absolutas ni dependa de archivos de este repositorio.
5. Probar el agente en un repositorio de prueba con un objetivo pequeño (generar un `README.md`).
6. Actualizar `docs/INDEX.md` si el cambio afecta a la documentación indexada.

## Por qué no hay `documentador.tpl.md`

OpenCode descubre **cualquier** archivo `.md` dentro de `.opencode/agent/` como un agente. Un `documentador.tpl.md` se registraría como un agente adicional (`documentador.tpl`) y duplicaría mantenimiento. La especificación y las guías de `docs/` cumplen el papel de plantilla; el único archivo generado es `.opencode/agent/documentador.md`.

## Reglas al generar

- **Minimalista** - No añadas herramientas ni permisos que el agente no necesite.
- **Frontmatter único** - Usa campos V2 (`permissions`, `disabled`, `steps`) o V1 (`tools`, `permission`), nunca una mezcla en el mismo archivo.
- **Evidencia obligatoria** - Mantén la autoevaluación y la firma `Validado con evidencia`.
- **Delegación** - Mantén la regla de `subagent(explore)` para exploraciones masivas.
- **Sin alucinaciones** - Mantén las restricciones absolutas.
- **Reutilizable** - El agente debe funcionar en cualquier repositorio, no solo en este.

## Ubicación

| Versión | Ruta preferida |
|---|---|
| OpenCode V2 | `.opencode/agents/documentador.md` |
| OpenCode V1 / compatibilidad | `.opencode/agent/documentador.md` |

Ambas rutas producen el mismo ID de agente (`documentador`). Este repositorio usa la ruta V1 documentada para mantener compatibilidad; V2 la descubre sin cambios.
