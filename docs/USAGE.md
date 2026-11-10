# USAGE.md

## Cómo cargarlo en OpenCode

### En otro repositorio
1. Copia `.opencode/agent/documentador.md` al repositorio objetivo en `.opencode/agent/documentador.md` (V2 también acepta `.opencode/agents/documentador.md`).
2. Copia `.opencode/commands/documentador.md` a `.opencode/commands/documentador.md`.
3. Abre ese repositorio en OpenCode.
4. Invoca `/documentador` o pide al agente principal que use el subagente `documentador`.

### En este repositorio
Ya está cargado: abre el proyecto y usa `/documentador`. Si la sesión ya estaba abierta antes de crear el agente, reiníciala para que OpenCode lo descubra.

## Cuándo usarlo
- **Documentar repo completo** - Genera README + ARCHITECTURE mínimos con evidencia.
- **Generar/actualizar README** - Enfocado a instalación y uso.
- **Actualizar docs** - Detección de desincronización con cambios mínimos.
- **Crear índice** - `docs/INDEX.md` con enlaces verificados (>= 2 documentos).
- **Crear changelog** - `CHANGELOG.md` solo si hay historial de git.
- **Entender repo desconocido** - Explorar, mapear y sintetizar sin generar archivos.

## Flujo
1. **INTAKE** - Entender objetivo y público.
2. **EXPLORACIÓN** - `glob`/`grep` o `subagent(explore)` si es masivo.
3. **MAPEO ARQUITECTÓNICO** - Punto de entrada, módulos y flujo.
4. **SÍNTESIS** - Qué hace frente a cómo está implementado.
5. **REDACCIÓN VERIFICADA** - Solo con evidencia.
6. **VALIDACIÓN CRUZADA** - Checklist obligatorio.
7. **ENTREGA** - Solo tras "Validado con evidencia".

## Reglas clave
- **Evidencia sobre suposición** - Todo se verifica con `read`/`glob`/`grep`.
- **Delegación inteligente** - `subagent(explore)` para exploración masiva; análisis, síntesis y validación se quedan en el agente.
- **Sin inventar** - No inventa archivos, rutas, comandos, variables ni APIs.
- **Mínimo viable** - Genera solo lo necesario.
- **Extras opcionales** - Diagramas, ADRs u OPERATIONS solo con evidencia y checklist.
- **Validación obligatoria** - Debe pasar `docs/VALIDATION_CHECKLIST.md` antes de entregar.
- **Nativo OpenCode** - Solo herramientas nativas.
- **Reutilizable** - Funciona en cualquier repositorio.

## Invocación

```text
/documentador Documenta este repositorio con evidencia.
/documentador Sincroniza la documentación con el código.
/documentador Genera docs/INDEX.md con enlaces verificados.
/documentador Genera CHANGELOG.md desde los commits recientes.
```

## Documentación relacionada
- [Índice de documentación](INDEX.md)
- [Especificación del agente](AGENT_SPEC_OPENCODE.md)
- [Guía de generación del subagente](SUBAGENT_TEMPLATE_GUIDE.md)
- [Checklist de validación](VALIDATION_CHECKLIST.md)
