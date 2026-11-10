# VALIDATION_CHECKLIST.md

## OBJETIVO
Checklist obligatorio que debe pasar el agente antes de entregar cualquier documentación. Forzar verificación con evidencia usando herramientas nativas de OpenCode.

## EXPLORACIÓN
- [ ] **Objetivo claro** - Se ha entendido el objetivo/público con evidencia
- [ ] **Ignorar correctamente** - Se ha aplicado `EXPLORATION_RULES.md`. Archivos clave nunca ignorados
- [ ] **Filtrado por relevancia** - Se han usado `glob`/`grep` para filtrar
- [ ] **Delegación correcta** - Si >15 archivos o múltiples directorios, se ha delegado a `subagent(explore)`. Tras recibir resultado, se han leído archivos concretos
- [ ] **Archivos prioritarios revisados** - Se han revisado manifiestos/README/entry points si existen

## MAPEO
- [ ] **Punto de entrada identificado** - Con evidencia (manifiesto o archivos raíz)
- [ ] **Módulos principales con rutas reales** - Verificados con `glob`/`read`
- [ ] **Flujo principal trazado** - 3-5 pasos desde entry point con rutas reales
- [ ] **Separado qué hace vs cómo** - Síntesis clara
- [ ] **Hecho vs inferido** - Diferenciado. Inferido marcado si aplica
- [ ] **Usado `ARCHITECTURE_MAPPING_GUIDE.md`** - Se ha seguido la guía

## REDACCIÓN
- [ ] **Usado `WRITING_RULES.md`** - Se ha seguido la guía
- [ ] **README accionable** - Permite instalar/configurar/ejecutar en <5 min (o solo lo verificable)
- [ ] **ARCHITECTURE real** - Basado en evidencia, sin descripciones genéricas
- [ ] **CONTRIBUTING** - Solo generado si hay evidencia, sino OMITIDO
- [ ] **Sin fluff** - Sin introducciones genéricas
- [ ] **Mínimo viable** - Solo lo necesario

## VERIFICACIÓN (rutas/comandos/vars/enlaces)
- [ ] **Rutas verificadas** - Todas las rutas mencionadas existen (comprobado con `glob`/`read`)
- [ ] **Comandos verificados** - Comandos existen en manifiestos (`package.json`/`Makefile`/`pyproject.toml`/`Cargo.toml`)
- [ ] **Variables verificadas** - Variables mencionadas existen en código o `.env.example` (si aplica)
- [ ] **Enlaces internos** - Enlaces relativos correctos (si existen)
- [ ] **Sin inventos** - Nada inventado. Todo rastreable a archivos leídos
- [ ] **Extras opcionales** - Si generados, cumplen checklist `DIAGRAMS_ADR_GUIDE.md` y son evidentes

## AUTOEVALUACIÓN (7 puntos)
- [ ] **1. Evidencia** - ¿Todo lo que afirmo está respaldado por archivos leídos?
- [ ] **2. Accionable** - ¿Puede un desarrollador seguir esto sin adivinar?
- [ ] **3. Verificable** - ¿He comprobado rutas/comandos/variables?
- [ ] **4. Mínimo viable** - ¿He generado solo lo necesario?
- [ ] **5. Nativo** - ¿Sigue los patrones/herramientas de OpenCode?
- [ ] **6. Reutilizable** - ¿Servirá para otros repositorios?
- [ ] **7. Sin deuda** - ¿He evitado inventar o asumir?

## FIRMA: "Validado con evidencia"
**Fecha/Contexto:** [Completar]  
**Resultado:** [ ] APROBADO - Todo verificado con evidencia  
**Firma:** Validado con evidencia usando herramientas nativas de OpenCode (`read`, `glob`, `grep`)
