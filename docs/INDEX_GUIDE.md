# INDEX_GUIDE.md

## OBJETIVO
Definir cómo generar un `docs/INDEX.md` claro, navegable y verificable que conecte toda la documentación relevante del repositorio. El índice debe basarse únicamente en archivos existentes y con enlaces relativos correctos.

## ARCHIVOS A INDEXAR
Indexar únicamente archivos que **existan realmente** en el repositorio:

| Archivo/Directorio | Uso |
|---|---|
| `README.md` | Punto de entrada principal |
| `ARCHITECTURE.md` | Arquitectura del proyecto |
| `CONTRIBUTING.md` | Guía para contribuir (solo si existe) |
| `docs/*.md` | Guías generales en la carpeta `docs/` |
| `docs/adr/*.md` | Architecture Decision Records (solo si existen) |
| `docs/OPERATIONS.md` | Guía operativa (solo si existe con evidencia) |
| `docs/USAGE.md` | Guía de uso (solo si existe) |
| `CHANGELOG.md` | Registro de cambios (solo si existe) |

## ESTRUCTURA SUGERIDA
Generar el índice con secciones mínimas y prácticas:

```markdown
# Índice de documentación

## Inicio
- [README](../README.md) - Descripción general, instalación y uso rápido

## Arquitectura
- [ARCHITECTURE](../ARCHITECTURE.md) - Arquitectura, módulos y flujo principal

## Decisiones técnicas
- [ADR-XXXX - Título](adr/XXXX-titulo-corto.md) - ... (solo si existen)

## Operaciones
- [OPERATIONS](OPERATIONS.md) - ... (solo si existe)

## Guías
- [Guía X](guia-x.md) - ... (solo archivos existentes)
```

**Reglas para la estructura:**
- Agrupar por categorías lógicas
- No crear secciones vacías
- Ordenar por relevancia (Inicio primero)
- Usar títulos claros y concisos

## REGLAS
- **Solo existentes** - Verificar con `glob` que cada archivo indexado existe. No inventar rutas.
- **Enlaces relativos correctos** - Usar rutas relativas válidas desde `docs/INDEX.md` (ej. `../README.md`, `adr/NNNN-...md`, etc.)
- **Mínimo** - No sobrecargar. Solo lo necesario para navegar la documentación.
- **Basado en evidencia** - Cada entrada debe corresponder a un archivo real.
- **Sin duplicados** - Una entrada por archivo.
- **Pragmático** - Si hay < 2 archivos de documentación relevantes, **NO GENERAR** `docs/INDEX.md`.
- **Sin fluff** - Sin descripciones genéricas innecesarias.

## PLANTILLA MINIMA
Plantilla base a seguir al generar `docs/INDEX.md`:

```markdown
# Índice de documentación

## Inicio
- [README](../README.md) - Visión general del proyecto

## Arquitectura
- [ARCHITECTURE](../ARCHITECTURE.md) - Estructura, módulos y flujo principal

## Guías
- [Nombre guía](ruta-relativa.md) - Breve descripción basada en contenido real

## Decisiones técnicas (ADRs)
- [ADR-0001 - Título](adr/0001-titulo-corto.md) - Decisión técnica documentada

## Operaciones
- [OPERATIONS](OPERATIONS.md) - Despliegue, configuración y operación
```

**Notas:**
- Eliminar cualquier sección que no tenga entradas
- Las descripciones deben ser cortas y basadas en el contenido real del archivo
- Verificar siempre los enlaces con `glob` antes de incluirlos
- Mantener coherente con `VALIDATION_CHECKLIST.md`
