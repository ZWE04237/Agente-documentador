# CHANGELOG_GUIDE.md

## OBJETIVO
Definir cómo generar un `CHANGELOG.md` pragmático, basado en evidencia, usando commits o cambios detectados. El objetivo es generar un registro mínimo y veraz, nunca inventar entradas.

## CUÁNDO GENERAR (git log/diff)
Generar `CHANGELOG.md` **únicamente** si hay evidencia verificable:

| Fuente | Uso |
|---|---|
| `.git/` | Si existe directorio `.git/`, considerar git como fuente |
| `git log --oneline -n 20` | Obtener commits recientes con evidencia real |
| `git diff --name-only` | Identificar archivos modificados sin commits aún |
| `git diff HEAD~1 HEAD --name-only` | Cambios entre último commit y anterior (si existe) |
| `git branch -a` | Contexto opcional, solo para entender historial |

**Regla:** Si **no existe `.git/`** o **no hay historial de commits verificable**, **NO GENERAR** `CHANGELOG.md`. Nunca fallar por falta de git.

## FORMATO PRAGMÁTICO
Usar un estilo inspirado en [Keep a Changelog](https://keepachangelog.com/es-ES/), pero minimalista:

| Sección | Uso |
|---|---|
| `Added` | Nuevas funcionalidades/documentación añadidas |
| `Changed` | Cambios en funcionalidad/documentación existente |
| `Fixed` | Correcciones |
| `Removed` | Elementos eliminados |
| `Docs` | Cambios exclusivamente de documentación (útil para este agente) |

**Formato general:**
```markdown
# Changelog

## [Unreleased]
### Added
- ...

### Changed
- ...

### Fixed
- ...

### Removed
- ...

### Docs
- ...
```

**Notas:**
- Usar fechas solo si hay contexto claro (fecha del commit). Si no hay fecha verificable, omitirla.
- Agrupar por tipo, solo con entradas evidenciadas.
- Priorizar entradas concretas y accionables sobre descripciones genéricas.

## REGLAS (solo evidenciado)
- **Solo evidencia** - Cada entrada debe provenir de `git log/diff` o cambios realmente detectados.
- **Sin inventar** - No crear entradas "genéricas" para cubrir todo el proyecto.
- **Mínimo** - Solo generar lo necesario. Si hay pocos cambios verificables, generar pocas entradas.
- **Sin reescritura** - Si ya existe `CHANGELOG.md`, **NO** reescribirlo completo. Solo proponer adición mínima si hay cambios nuevos y evidentes.
- **Opcional con git** - Si no hay git/historial -> OMITIR completamente.
- **Basado en hechos** - Extraer mensaje de commit o inferir tipo solo si es obvio y verificable.
- **Coherente** - Seguir `VALIDATION_CHECKLIST.md`.

## PLANTILLA
Plantilla mínima a usar al generar `CHANGELOG.md` desde cero:

```markdown
# Changelog

## [Unreleased]

### Added
- Añadida documentación inicial basada en análisis del repositorio

### Docs
- Generado README.md y ARCHITECTURE.md con evidencia
```

**Instrucciones para usar la plantilla:**
- Eliminar secciones vacías
- Reemplazar con entradas reales extraídas de git
- No usar la plantilla como "relleno" si no hay evidencia
- Mantener el formato limpio y legible
- Si solo hay cambios de docs, usar principalmente `Docs`
