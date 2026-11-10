# ROADMAP: AGENTE DOCUMENTADOR PARA OPENCODE (BIG PICKLE)

**Ruta de trabajo:** `este repositorio`  
**IA Desarrolladora:** Big Pickle (dentro de OpenCode)  
**Objetivo:** Construir un agente documentador nativo para OpenCode, empaquetado como subagente reutilizable en `.opencode/agent/`  
**Filosofía:** Explorar -> Mapear -> Comprender -> Sintetizar -> Documentar | Evidencia sobre suposición  
**Referencia obligatoria:** `PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md`

---

## FASE 0: BOOTSTRAP OPENCODE-NATIVO
**Objetivo:** Crear la estructura base, documentación interna y convenciones para construir el agente dentro de OpenCode.  
**Estado:** `COMPLETADA`

### Paso 0.1: Inicializar estructura base
**Estado:** `COMPLETADO`
### Paso 0.2: Crear plantilla de prompts
**Estado:** `COMPLETADO`
### Paso 0.3: Sincronizar referencia cruzada
**Estado:** `COMPLETADO`

**FASE 0 COMPLETA.**

---

## FASE 1: DEFINIR EL SUBAGENTE "DOCUMENTADOR" (DISEÑO)
**Objetivo:** Diseñar la especificación del agente reutilizable antes de escribir su definición ejecutable.  
**Estado:** `COMPLETADA`

### Paso 1.1: Especificación del agente
**Estado:** `COMPLETADO`
### Paso 1.2: Plantilla de subagente OpenCode
**Estado:** `COMPLETADO`

**FASE 1 COMPLETA.**

---

## FASE 2: MOTOR DE EXPLORACIÓN
**Objetivo:** Reglas claras para descubrir, filtrar e ignorar archivos.  
**Estado:** `COMPLETADA`

### Paso 2.1: Reglas de descubrimiento e ignore-list
**Estado:** `COMPLETADO`
### Paso 2.2: Integrar reglas al agente
**Estado:** `COMPLETADO`

**FASE 2 COMPLETA.**

---

## FASE 3: MAPEO ARQUITECTÓNICO, SÍNTESIS Y COMPRENSIÓN
**Objetivo:** Mapa verificable con evidencia.  
**Estado:** `COMPLETADA`

### Paso 3.1: Guía de mapeo arquitectónico
**Estado:** `COMPLETADO`
### Paso 3.2: Integrar mapeo al agente
**Estado:** `COMPLETADO`

**FASE 3 COMPLETA.**

---

## FASE 4: REDACTOR INTELIGENTE Y VERIFICADO
**Objetivo:** Generar documentación útil con reglas estrictas de verificación.  
**Estado:** `COMPLETADA`

### Paso 4.1: Reglas de redacción verificada
**Estado:** `COMPLETADO`
### Paso 4.2: Integrar redacción al agente
**Estado:** `COMPLETADO`

**FASE 4 COMPLETA.**

---

## FASE 5: DIAGRAMAS, ADRs, GUÍAS OPERATIVAS
**Objetivo:** Añadir valor sin inflar. Solo cuando hay evidencia.  
**Estado:** `COMPLETADA`

### Paso 5.1: Guía de diagramas, ADRs y guías operativas
**Estado:** `COMPLETADO`
### Paso 5.2: Integrar opcional al agente
**Estado:** `COMPLETADO`

**FASE 5 COMPLETA.**

---

## FASE 6: VALIDACIÓN CRUZADA, SINCRONIZACIÓN Y AUTOEVALUACIÓN
**Objetivo:** Forzar validación antes de entregar.  
**Estado:** `COMPLETADA`

### Paso 6.1: Checklist de validación obligatoria
**Estado:** `COMPLETADO`
### Paso 6.2: Integrar validación obligatoria al agente
**Estado:** `COMPLETADO`

**FASE 6 COMPLETA.**

---

## FASE 7: EMPAQUETADO, TEST E2E Y ENTREGA FINAL
**Objetivo:** Generar subagente real, probar y cerrar.  
**Estado:** `COMPLETADA`

### Paso 7.1: Generar subagente real
**Estado:** `COMPLETADO`
### Paso 7.2: Test end-to-end
**Estado:** `COMPLETADO`
### Paso 7.3: Pulido final y cierre
**Estado:** `COMPLETADO`

**FASE 7 COMPLETA.**

---

## FASE 8: DOCUMENTACIÓN VIVA - DETECCIÓN DE DESINCRONIZACIÓN
**Objetivo:** Detectar cuando la documentación queda desactualizada con respecto al código y proponer actualizaciones mínimas basadas en evidencia.  
**Estado:** `COMPLETADA`  
**Prioridad:** CRÍTICA

### Paso 8.1: Guía de detección de desincronización
**Estado:** `COMPLETADO`  
**Prioridad:** CRÍTICA  
**Tiempo estimado:** 10-15 min

**Objetivo:** Crear `docs/DOC_SYNC_GUIDE.md` con reglas para detectar desincronización entre código y documentación.

**Tareas:**
- [x] Crear `docs/DOC_SYNC_GUIDE.md` con:
  - **Fuentes de verdad**: `package.json`, `src/`, `app/`, `lib/`, `index.*`, `main.*`, `scripts`
  - **Qué comparar**: scripts en manifiesto vs README, punto de entrada vs ARCHITECTURE, rutas mencionadas vs existencia real
  - **Detección con git**: Si existe `.git/`, usar `git diff --name-only`, `git log -1 --oneline` para enfocar cambios
  - **Reglas**: Solo proponer cambios si hay evidencia. Nunca reescribir completo
  - **Salida**: Lista de hallazgos con archivo afectado, tipo (falta / desactualizado / roto), evidencia

**Entregables:**
- `docs/DOC_SYNC_GUIDE.md`

**Criterios de aceptación:**
- [x] Solo basado en evidencia
- [x] Funciona sin git o con git
- [x] Propone cambios mínimos
- [x] Alineado con el prompt maestro

#### PROMPT ESPECÍFICO PARA BIG PICKLE (FASE 8 - PASO 8.1)
```text
# PROMPT: FASE 8 - PASO 8.1 | Guía de detección de desincronización

Actúa siguiendo estrictamente PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md.

RUTA DE TRABAJO: este repositorio

TAREAS:
1. Crear docs/DOC_SYNC_GUIDE.md con:
   - OBJETIVO (documentación viva)
   - FUENTES DE VERDAD
   - QUÉ COMPARAR (README vs manifiesto, ARCHITECTURE vs entry point/rutas)
   - USO DE GIT (opcional)
   - HEURÍSTICAS (rutas rotas, scripts inexistentes)
   - REPORTE DE DESINCRONIZACIÓN (formato)
   - REGLAS: solo evidencia, mínimo, sin inventar

REGLAS:
- Solo en esta ruta
- Pragmático
- Sin sobre-generación

VALIDAR: Coherente con VALIDATION_CHECKLIST.md
ENTREGABLE: docs/DOC_SYNC_GUIDE.md
```

### Paso 8.2: Integrar sincronización al subagente
**Estado:** `COMPLETADO`  
**Prioridad:** CRÍTICA  
**Tiempo estimado:** 8-12 min

**Objetivo:** Añadir capacidad de "sync check" al agente.

**Tareas:**
- [x] Añadir sección `# SINCRONIZACIÓN CÓDIGO <-> DOCUMENTACIÓN` a `.opencode/agent/documentador.md`
- [x] Obligar a ejecutar sync check si existen `README.md`/`ARCHITECTURE.md` y se pide actualizar o hay cambios
- [x] Generar reporte con hallazgos + propuesta mínima

**Entregables:**
- `.opencode/agent/documentador.md` actualizado

**Criterios de aceptación:**
- [x] Usa `glob`/`grep`/`read` (y `git` solo si existe)
- [x] Propone cambios mínimos basados en evidencia
- [x] No reescribe documentación completa

#### PROMPT ESPECÍFICO PARA BIG PICKLE (FASE 8 - PASO 8.2)
```text
# PROMPT: FASE 8 - PASO 8.2 | Integrar sync al agente

Actúa siguiendo estrictamente PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md.

RUTA DE TRABAJO: este repositorio

TAREAS:
1. Leer docs/DOC_SYNC_GUIDE.md y el agente actual
2. Añadir sección "SINCRONIZACIÓN CÓDIGO <-> DOCUMENTACIÓN":
   - Consultar DOC_SYNC_GUIDE.md
   - Si git existe: revisar archivos modificados
   - Comparar scripts/entry points/rutas
   - Generar reporte con hallazgos + propuesta mínima
   - Solo proponer si hay evidencia
3. Actualizar ambos archivos

VALIDAR: Sin reescritura masiva
ENTREGABLE: .opencode/agent/documentador.md
```

**FASE 8 COMPLETA CUANDO:** Guía + integración con detección proactiva y propuesta mínima.

---

## FASE 9: MAPA DE CONOCIMIENTO - INDEX.md
**Objetivo:** Crear un índice navegable que conecte toda la documentación del repositorio.  
**Estado:** `COMPLETADA`  
**Prioridad:** ALTA

### Paso 9.1: Guía para generar INDEX.md
**Estado:** `COMPLETADO`  
**Prioridad:** ALTA  
**Tiempo estimado:** 8-10 min

**Objetivo:** Crear `docs/INDEX_GUIDE.md` con reglas para generar `docs/INDEX.md`.

**Tareas:**
- [x] Crear `docs/INDEX_GUIDE.md` con:
  - **Qué indexar**: `README.md`, `ARCHITECTURE.md`, `CONTRIBUTING.md`, `docs/*.md`, `docs/adr/*.md`, `docs/OPERATIONS.md`
  - **Estructura**: Por secciones (Inicio, Arquitectura, Decisiones, Operaciones, Guías)
  - **Enlaces relativos**: Correctos y verificados
  - **Solo existente**: No indexar archivos inexistentes
  - **Mínimo**: Claro y navegable

**Entregables:**
- `docs/INDEX_GUIDE.md`

**Criterios de aceptación:**
- [x] Solo enlaces verificados
- [x] Sin inventar archivos
- [x] Navegable

#### PROMPT ESPECÍFICO PARA BIG PICKLE (FASE 9 - PASO 9.1)
```text
# PROMPT: FASE 9 - PASO 9.1 | Guía INDEX.md

Actúa siguiendo estrictamente PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md.

RUTA DE TRABAJO: este repositorio

TAREAS:
1. Crear docs/INDEX_GUIDE.md con:
   - OBJETIVO
   - ARCHIVOS A INDEXAR
   - ESTRUCTURA SUGERIDA
   - REGLAS (solo existentes, enlaces relativos)
   - PLANTILLA MINIMA

REGLAS:
- Solo en esta ruta
- Verificable
- Minimalista

VALIDAR: Coherente
ENTREGABLE: docs/INDEX_GUIDE.md
```

### Paso 9.2: Integrar generación de INDEX al agente
**Estado:** `COMPLETADO`  
**Prioridad:** ALTA  
**Tiempo estimado:** 5-8 min

**Objetivo:** Añadir generación opcional de `docs/INDEX.md` cuando exista documentación.

**Tareas:**
- [x] Añadir sección `# MAPA DE CONOCIMIENTO` al agente
- [x] Generar `docs/INDEX.md` solo si hay >=2 archivos de docs existentes
- [x] Verificar enlaces con `glob`
- [x] Solo con evidencia

**Entregables:**
- `.opencode/agent/documentador.md` actualizado
- `docs/INDEX.md` generado

#### PROMPT ESPECÍFICO PARA BIG PICKLE (FASE 9 - PASO 9.2)
```text
# PROMPT: FASE 9 - PASO 9.2 | Integrar INDEX al agente

Actúa siguiendo estrictamente PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md.

RUTA DE TRABAJO: este repositorio

TAREAS:
1. Leer docs/INDEX_GUIDE.md
2. Añadir sección "MAPA DE CONOCIMIENTO":
   - Consultar guía
   - Solo si >=2 docs existentes
   - Generar docs/INDEX.md con enlaces verificados
   - Nunca inventar archivos
3. Actualizar el agente real

VALIDAR: Enlaces verificados
ENTREGABLE: Agente actualizado + docs/INDEX.md
```

**FASE 9 COMPLETA CUANDO:** Guía + generación opcional de INDEX con enlaces verificados.

---

## FASE 10: RESUMEN DE CAMBIOS - CHANGELOG.md
**Objetivo:** Generar `CHANGELOG.md` basado en commits o cambios detectados, con evidencia.  
**Estado:** `COMPLETADA`  
**Prioridad:** ALTA

### Paso 10.1: Guía para generar CHANGELOG
**Estado:** `COMPLETADO`  
**Prioridad:** ALTA  
**Tiempo estimado:** 8-10 min

**Objetivo:** Crear `docs/CHANGELOG_GUIDE.md`

**Tareas:**
- [x] Crear guía con:
  - **Fuentes**: `git log`, `git diff`, cambios recientes
  - **Formato**: Keep a Changelog style (Added/Changed/Fixed/Removed) pero pragmático
  - **Evidencia**: Basado en commits reales o cambios detectados
  - **Sin inventar**: Si no hay git/history -> NO GENERAR
  - **Mínimo**: Solo entradas verificables

**Entregables:**
- `docs/CHANGELOG_GUIDE.md`

**Criterios de aceptación:**
- [x] Solo con evidencia
- [x] Funciona con git o sin git
- [x] No inventa entradas

#### PROMPT ESPECÍFICO PARA BIG PICKLE (FASE 10 - PASO 10.1)
```text
# PROMPT: FASE 10 - PASO 10.1 | Guía CHANGELOG

Actúa siguiendo estrictamente PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md.

RUTA DE TRABAJO: este repositorio

TAREAS:
1. Crear docs/CHANGELOG_GUIDE.md
   - OBJETIVO
   - CUÁNDO GENERAR (git log/diff)
   - FORMATO PRAGMÁTICO
   - REGLAS (solo evidenciado)
   - PLANTILLA

REGLAS:
- Basado en evidencia
- Mínimo
- Si no hay git/historial -> omitir

VALIDAR: Coherente
ENTREGABLE: docs/CHANGELOG_GUIDE.md
```

### Paso 10.2: Integrar generación de CHANGELOG al agente
**Estado:** `COMPLETADO`  
**Prioridad:** ALTA  
**Tiempo estimado:** 5-8 min

**Objetivo:** Añadir generación opcional de `CHANGELOG.md`

**Tareas:**
- [x] Añadir sección `# RESUMEN DE CAMBIOS (CHANGELOG)` al agente
- [x] Generar solo si hay `.git` o commits verificables
- [x] Usar evidencia
- [x] No generar por defecto

**Entregables:**
- `.opencode/agent/documentador.md` actualizado
- `CHANGELOG.md` omitido correctamente (sin git en este repositorio)

#### PROMPT ESPECÍFICO PARA BIG PICKLE (FASE 10 - PASO 10.2)
```text
# PROMPT: FASE 10 - PASO 10.2 | Integrar CHANGELOG al agente

Actúa siguiendo estrictamente PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md.

RUTA DE TRABAJO: este repositorio

TAREAS:
1. Leer docs/CHANGELOG_GUIDE.md
2. Añadir sección opcional:
   - Solo si existe .git o hay commits
   - Usar git log/diff si existen
   - Generar CHANGELOG.md solo con entradas verificables
   - Nunca inventar
3. Actualizar el agente real

VALIDAR: Sin inventos
ENTREGABLE: Actualizados
```

**FASE 10 COMPLETA CUANDO:** Guía + generación opcional de CHANGELOG con evidencia.

---

## FASE 11: INTEGRACIÓN FINAL, TEST Y AJUSTE DE AGENTE
**Objetivo:** Integrar todas las nuevas capacidades al agente real, probarlas con evidencia y dejarlo completo.  
**Estado:** `COMPLETADA`  
**Prioridad:** CRÍTICA

### Paso 11.1: Regenerar agente real con todas las capacidades
**Estado:** `COMPLETADO`  
**Prioridad:** CRÍTICA  
**Tiempo estimado:** 10-15 min

**Objetivo:** Actualizar `.opencode/agent/documentador.md` con todas las secciones de fases 8-10.

**Tareas:**
- [x] Leer todas las guías nuevas: `DOC_SYNC_GUIDE.md`, `INDEX_GUIDE.md`, `CHANGELOG_GUIDE.md`
- [x] Integrar secciones: `SINCRONIZACIÓN CÓDIGO <-> DOCUMENTACIÓN`, `MAPA DE CONOCIMIENTO`, `RESUMEN DE CAMBIOS (CHANGELOG)`
- [x] Mantener flujo, restricciones, validación obligatoria
- [x] Solo herramientas nativas, evidencia obligatoria

**Entregables:**
- `.opencode/agent/documentador.md` actualizado

**Criterios de aceptación:**
- [x] Todas las secciones integradas
- [x] Sin herramientas añadidas
- [x] Validación sigue siendo obligatoria

#### PROMPT ESPECÍFICO PARA BIG PICKLE (FASE 11 - PASO 11.1)
```text
# PROMPT: FASE 11 - PASO 11.1 | Regenerar agente con fases 8-10

Actúa siguiendo estrictamente PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md.

RUTA DE TRABAJO: este repositorio

TAREAS:
1. Leer todas las guías 8-10 y el agente actual
2. Generar .opencode/agent/documentador.md completo con:
   - Sincronización código<->docs
   - Mapa de conocimiento (INDEX)
   - Resumen de cambios (CHANGELOG)
   - Todo anterior + validación obligatoria
3. Mantener minimalista pero completo

VALIDAR: Sin inventos
ENTREGABLE: .opencode/agent/documentador.md
```

### Paso 11.2: Test con detección de desincronización
**Estado:** `COMPLETADO`  
**Prioridad:** CRÍTICA  
**Tiempo estimado:** 12-15 min

**Objetivo:** Probar sync check con evidencia.

**Tareas:**
- [x] Crear test minimal (únicamente en este proyecto): `test-sync/`
- [x] Crear repo con `package.json` con script `dev` y `README.md` sin él
- [x] Aplicar sync check y verificar que detecta desincronización con evidencia
- [x] Proponer actualización mínima
- [x] Eliminar `test-sync/`

**Entregables:**
- `docs/SYNC_TEST_REPORT.md`

**Criterios de aceptación:**
- [x] Detecta con evidencia
- [x] Propuesta mínima
- [x] Sin reescritura completa

#### PROMPT ESPECÍFICO PARA BIG PICKLE (FASE 11 - PASO 11.2)
```text
# PROMPT: FASE 11 - PASO 11.2 | Test sync check

Actúa siguiendo estrictamente PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md.

RUTA DE TRABAJO: este repositorio

TAREAS:
1. Crear test-sync/sample/ con package.json (script dev) y README sin dev
2. Ejecutar sync check siguiendo DOC_SYNC_GUIDE
3. Documentar en docs/SYNC_TEST_REPORT.md
4. Limpiar test-sync/

VALIDAR: Basado en evidencia
ENTREGABLE: docs/SYNC_TEST_REPORT.md
```

### Paso 11.3: Test de INDEX y CHANGELOG
**Estado:** `COMPLETADO`  
**Prioridad:** ALTA  
**Tiempo estimado:** 8-10 min

**Objetivo:** Probar generación opcional de INDEX y CHANGELOG con evidencia.

**Tareas:**
- [x] Crear test-docs/ con varios archivos
- [x] Probar generación de `docs/INDEX.md`
- [x] Probar generación de `CHANGELOG.md` (con o sin git)
- [x] Verificar enlaces
- [x] Eliminar test-docs/

**Entregables:**
- `docs/INDEX_CHANGELOG_TEST_REPORT.md`

#### PROMPT ESPECÍFICO PARA BIG PICKLE (FASE 11 - PASO 11.3)
```text
# PROMPT: FASE 11 - PASO 11.3 | Test INDEX + CHANGELOG

Actúa siguiendo estrictamente PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md.

RUTA DE TRABAJO: este repositorio

TAREAS:
1. Crear test-docs/ con README, ARCHITECTURE, docs/guide.md
2. Generar docs/INDEX.md con enlaces verificados
3. Probar CHANGELOG (si existe git usarlo, si no omitir)
4. Documentar en docs/INDEX_CHANGELOG_TEST_REPORT.md
5. Limpiar test-docs/

VALIDAR: Solo archivos existentes indexados
ENTREGABLE: Reporte + limpieza
```

### Paso 11.4: Cierre con checklist final
**Estado:** `COMPLETADO`  
**Prioridad:** CRÍTICA  
**Tiempo estimado:** 5-8 min

**Objetivo:** Validar todo completo.

**Tareas:**
- [x] Revisar que todas las fases 0-11 estén completas
- [x] Actualizar `README.md` si necesario
- [x] Crear `docs/ROADMAP_CLOSURE.md` con resumen
- [x] Ejecutar checklist final

**Entregables:**
- `docs/ROADMAP_CLOSURE.md`

#### PROMPT ESPECÍFICO PARA BIG PICKLE (FASE 11 - PASO 11.4)
```text
# PROMPT: FASE 11 - PASO 11.4 | Cierre final

Actúa siguiendo estrictamente PROMPT_MAESTRO_AGENTE_DOCUMENTADOR_OPENCODE.md.

RUTA DE TRABAJO: este repositorio

TAREAS:
1. Verificar que todos los archivos existan
2. Actualizar README si es necesario
3. Crear docs/ROADMAP_CLOSURE.md con el resumen de todas las fases
4. Ejecutar el checklist de validación

VALIDAR: Completo
ENTREGABLE: docs/ROADMAP_CLOSURE.md
```

**FASE 11 COMPLETA CUANDO:** Agente actualizado con todas las capacidades, probadas y documentadas.

---

## RESUMEN GENERAL ACTUALIZADO

| Fase | Estado | Notas |
|---|---|---|
| **FASE 0** | `COMPLETADA` | Bootstrap |
| **FASE 1** | `COMPLETADA` | Diseño |
| **FASE 2** | `COMPLETADA` | Exploración |
| **FASE 3** | `COMPLETADA` | Mapeo y síntesis |
| **FASE 4** | `COMPLETADA` | Redactor verificado |
| **FASE 5** | `COMPLETADA` | Diagramas/ADRs/guías (solo Mermaid, opcionales) |
| **FASE 6** | `COMPLETADA` | Validación obligatoria |
| **FASE 7** | `COMPLETADA` | Empaquetado, test E2E, cierre |
| **FASE 8** | `COMPLETADA` | Documentación viva - detección de desincronización |
| **FASE 9** | `COMPLETADA` | INDEX.md - mapa de conocimiento |
| **FASE 10** | `COMPLETADA` | CHANGELOG.md - resumen de cambios (omitido sin git) |
| **FASE 11** | `COMPLETADA` | Integración final, tests y cierre |

**ESTADO:** Fases 0-11 completadas. Solo diagramas **Mermaid**. Enfoque basado en evidencia y cambios mínimos.
**OBJETIVO FINAL:** Agente documentador completo, reutilizable, con documentación viva, índice navegable, changelog basado en evidencia y detección proactiva de desincronización. 
