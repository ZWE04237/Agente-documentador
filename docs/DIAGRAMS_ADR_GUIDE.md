# DIAGRAMS_ADR_GUIDE.md

## OBJETIVO
Añadir valor sin inflar la documentación. Solo generar diagramas, ADRs o guías operativas **si hay evidencia verificable**. Nunca por defecto.

## MERMAID (cuándo usar/no usar)

### CUÁNDO USAR
Usar Mermaid **solo** si añade claridad real:
- **Flujo principal** - Cuando el flujo trazado desde el entry point necesita visualizarse para entenderlo mejor
- **Componentes** - Cuando hay módulos principales claramente definidos y sus relaciones son evidentes
- **Secuencia** - Solo si se ha verificado una interacción concreta entre módulos

### CUÁNDO NO USAR
- **Por defecto** - Nunca generar diagramas solo "porque sí"
- **Genéricos** - No crear diagramas teóricos sin evidencia
- **Innecesarios** - Si el texto ya explica el flujo claramente, NO añadir diagrama
- **Inventados** - No inventar relaciones entre módulos

**Regla:** **Texto + rutas reales > diagrama inventado**. Usar solo si realmente mejora la comprensión.

## ADR TEMPLATE + reglas

### Ubicación
Crear ADRs únicamente en: `docs/adr/NNNN-titulo-corto.md`  
Usar numeración incremental: `0001-...`, `0002-...`

### Plantilla
```markdown
# ADR-NNNN: [Título corto]

## Estado
[Propuesto | Aceptado | Rechazado | Obsoleto]

## Contexto
[Descripción de la situación que llevó a la decisión. Basado en evidencia del código/repositorio]

## Decisión
[Decisión tomada tal como se puede inferir o documentar con evidencia]

## Consecuencias
[Consecuencias positivas y negativas reales o razonables basadas en lo observado]

## Fecha
[YYYY-MM-DD]
```

### Reglas ADR
- **Solo con evidencia** - Crear ADR SOLO si hay evidencia concreta de una decisión técnica (estructura, patrón, configuración decidida, etc.)
- **No especular** - No inventar decisiones pasadas
- **Pragmático** - Un ADR útil vale más que 10 ADRs inventados
- **Verificable** - Debe poder relacionarse con archivos/código real

## OPERATIONS.md (pragmático)

Crear `docs/OPERATIONS.md` **SOLO** si hay información verificable sobre despliegue/operación.

### Candidatos válidos
- `Dockerfile` / `docker-compose*`
- Scripts de despliegue en `package.json`/`Makefile`
- Variables de entorno documentadas o en `.env.example`
- Configuración de CI/CD verificable (`.github/`, `.gitlab-ci.yml`, etc.)
- Instrucciones de build reales

### Plantilla mínima
```markdown
# Operaciones

## Requisitos
[Solo si verificable]

## Variables de entorno
[Solo si existen en .env.example o código]

## Build
[Comandos reales verificados]

## Despliegue
[Solo si hay evidencia de proceso de despliegue]

## Troubleshooting
[Solo si hay info verificable, sino OMITIR]
```

**Regla:** Si no hay evidencia suficiente, **NO CREARLO**.

## CHECKLIST "¿Vale la pena?"

Antes de generar cualquier extra, responder SI a **TODOS**:

- [ ] **Evidencia** - ¿Existe evidencia directa en el repositorio?
- [ ] **Utilidad** - ¿Añade claridad real al desarrollador nuevo?
- [ ] **Verificable** - ¿Puedo comprobar rutas/comandos/archivos?
- [ ] **No inventado** - ¿No estoy suponiendo decisiones o pasos?
- [ ] **Mínimo** - ¿Es lo justo y necesario?
- [ ] **No forzado** - ¿No lo estoy generando solo por completar?

**Si alguna respuesta es NO -> NO GENERARLO.**

**Regla final:** **Extras opcionales, nunca obligatorios.** Prioridad siempre: `README.md` + `ARCHITECTURE.md` con evidencia.
