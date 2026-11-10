# WRITING_RULES.md

## OBJETIVO
Establecer reglas estrictas para generar documentación con evidencia. Todo lo que se escriba debe poder verificarse con `glob`/`grep`/`read`.

## README (checklist verificación)
El `README.md` debe permitir a un desarrollador nuevo **instalar, configurar y ejecutar** en <5 minutos.

**Checklist obligatorio:**
- [ ] **Descripción** - Breve, basada en el proyecto real (verificado)
- [ ] **Requisitos** - Solo si existen (lenguaje/versión en manifiesto)
- [ ] **Instalación** - Usar comandos reales encontrados en manifiesto/scripts
- [ ] **Uso** - Comandos verificables (`package.json` scripts, `Makefile`, etc.)
- [ ] **Estructura breve** - Solo carpetas/archivos clave reales
- [ ] **Tests** - Solo si existen scripts de test
- [ ] **Licencia** - Solo si existe archivo `LICENSE*`

**Regla:** Si un apartado no puede verificarse, **OMITIRLO**. No lo inventes.

## ARCHITECTURE (evidencia obligatoria)
`ARCHITECTURE.md` debe describir la arquitectura **real** del proyecto.

**Requisitos:**
- [ ] **Punto de entrada** - Identificado con evidencia (manifiesto o archivos raíz)
- [ ] **Módulos principales** - Con rutas reales y responsabilidad breve
- [ ] **Flujo principal** - 3-5 pasos trazados desde entry point
- [ ] **Dependencias relevantes** - Solo las necesarias para entender arquitectura
- [ ] **Diagramas Mermaid** - **SOLO** si añaden claridad real. Nunca obligatorios
- [ ] **Hecho vs inferido** - Aclarar si hay inferencias mínimas

**Regla:** Enfocar en **módulos y flujo**, no en detalle de cada función/clase.

## CONTRIBUTING (pragmático)
Crear `CONTRIBUTING.md` **SOLO** si hay información verificable.

**Candidatos válidos:**
- Scripts en manifiesto (`npm run`, `make`, etc.)
- Estructura clara para contribuir
- Reglas existentes (`CONTRIBUTING*`, `CODEOWNERS`)
- Tests verificables

**Si no hay evidencia:** **NO CREARLO**. Mejor omitir que inventar.

## VALIDACIÓN DE COMANDOS (contra package.json/Makefile/etc)
Todo comando mencionado debe existir:

| Fuente | Acción |
|---|---|
| `package.json` | Comprobar `scripts.*` |
| `Makefile` | Comprobar targets |
| `pyproject.toml` | Comprobar scripts/entry points |
| `Cargo.toml` | Comprobar binarios/targets |
| `go.mod` / otros | Comprobar según manifiesto |

**Regla:** Usa el comando **tal como aparece** o describe lo verificable. Nunca inventes `npm run dev` si no existe.

## VALIDACIÓN DE RUTAS
Antes de mencionar cualquier ruta/archivo:

- [ ] Verificar con `glob` o `read`
- [ ] Confirmar que existe en el repositorio objetivo
- [ ] Solo mencionar rutas relevantes
- [ ] No usar rutas genéricas o hipotéticas

## PROHIBICIONES
- **SIN FLUFF** - Elimina introducciones genéricas ("En la era digital...", "Hoy en día...")
- **SIN INVENTAR** - No inventes comandos, scripts, variables, rutas, APIs o dependencias
- **SIN SOBREGENERAR** - Genera solo lo necesario para el objetivo
- **SIN DESCRIPCIONES VACÍAS** - Cada sección debe ser accionable
- **SIN ASUMIR** - Si no está claro, no lo afirmes. Usa `question` solo si bloquea
- **SIN DIAGRAMAS POR DEFECTO** - Solo si realmente ayudan

## PLANTILLAS MINIMALES

### Plantilla README mínimo (solo lo verificable)
```markdown
# [Nombre del proyecto - solo si aparece en README/manifiesto]

## Descripción
[Descripción breve basada en evidencia]

## Requisitos
[Solo si verificable]

## Instalación
[Comandos reales verificados]

## Uso
[Comandos reales verificados]

## Estructura
[Carpetas/archivos clave reales]

## Tests
[Solo si existe script de test]
```

### Plantilla ARCHITECTURE mínimo
```markdown
# Arquitectura

## Punto de entrada
- Ruta: [ruta real]
- Evidencia: [manifiesto/archivo]

## Módulos principales
| Módulo | Responsabilidad |
|---|---|
| [ruta real] | [basado en lectura] |

## Flujo principal
1. [paso con ruta real]
2. [paso con ruta real]
3. [paso con ruta real]

## Notas
[Hecho/Inferido si aplica]
```

**Regla final:** **Verificar > Afirmar**. Si no hay evidencia, no lo escribas.
