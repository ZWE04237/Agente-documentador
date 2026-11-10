# ARCHITECTURE_MAPPING_GUIDE.md

## OBJETIVO
Transformar los hallazgos de la exploración en un **mapa arquitectónico verificable**. Identificar punto de entrada, módulos, dependencias y flujo principal con evidencia directa del código fuente.

## PUNTO DE ENTRADA (cómo identificar)
Buscar con evidencia usando `glob`/`grep`/`read`:

| Fuente | Acción |
|---|---|
| `package.json` | Revisar `main`, `module`, `bin`, `scripts.start` |
| `pyproject.toml` | Revisar `[project.scripts]` o entry points |
| `Cargo.toml` | Revisar `[[bin]]` o `default-run` |
| `go.mod` | Buscar `main()` en raíz o cmd/ |
| `pom.xml` | Revisar `mainClass` |
| Archivos raíz | Buscar `index.*`, `main.*`, `app.*`, `server.*`, `cli.*` |

**Regla:** Solo declarar punto de entrada si existe físicamente y es verificable.

## MÓDULOS Y RESPONSABILIDADES
Mapear módulos reales con rutas:

1. Identificar carpetas relevantes (`src/`, `app/`, `lib/`, `core/`, `api/`, `server/`, `packages/`)
2. Leer archivos clave para entender responsabilidad
3. Describir **qué hace** cada módulo, no todo el código
4. Agrupar solo si comparten responsabilidad clara

**Salida:** Lista con `ruta` + `responsabilidad (breve)`.

## DEPENDENCIAS
Identificar dependencias con evidencia:

| Tipo | Cómo |
|---|---|
| **Externas** | Leer manifiesto (`package.json`, `pyproject.toml`, etc.) |
| **Internas** | Usar `grep` para buscar `import`/`require`/`from` entre módulos |
| **Configuración** | Solo si afecta arquitectura/flujo |

No listar todas las dependencias, listar las **relevantes para entender la arquitectura**.

## FLUJO PRINCIPAL
Trazar desde el punto de entrada:

1. Leer entry point
2. Seguir imports/referencias relevantes con `grep`
3. Identificar ruta crítica (inicio -> lógica principal -> salida)
4. Describir en 3-5 pasos máximo
5. Basarse en código real, no en suposiciones

## SÍNTESIS (qué hace vs cómo)
- **Qué hace:** Propósito del sistema/módulo (alto nivel)
- **Cómo está implementado:** Solo lo esencial para entender la estructura
- **Evitar:** Detallar cada función/clase. Enfocar en módulos y flujo.

## HECHO VS INFERIDO
| Tipo | Acción |
|---|---|
| **HECHO** | Solo lo leído/verificado con `read`/`glob`/`grep` |
| **INFERIDO** | Si es necesario, marcar explícitamente como *inferido* y justificar con evidencia mínima |
| **PROHIBIDO** | Afirmar sin evidencia |

## VALIDACIÓN (comprobar rutas)
Antes de incluir cualquier ruta/módulo/archivo:

- [ ] Verificar existencia con `glob` o `read`
- [ ] Comprobar que es relevante para arquitectura/uso
- [ ] No inventar rutas
- [ ] Solo incluir lo que has leído o verificado

## PLANTILLA DE MAPA (lista con rutas reales)
Usar esta plantilla al generar el mapa:

```markdown
## MAPA ARQUITECTÓNICO

### Punto de entrada
- Ruta: [ruta real verificada]
- Razón: [evidencia: package.json main/scripts o archivo encontrado]

### Módulos principales
| Módulo (ruta) | Responsabilidad |
|---|---|
| [ruta real] | [descripción breve basada en lectura] |

### Dependencias relevantes
- Internas: [rutas reales]
- Externas: [solo las clave del manifiesto]

### Flujo principal
1. [paso con ruta/archivo real]
2. [paso con ruta/archivo real]
3. [paso con ruta/archivo real]

### Notas
- Hecho vs inferido: [aclarar si aplica]
```

**Regla final:** Si no puedes verificarlo, **no lo incluyas**.
