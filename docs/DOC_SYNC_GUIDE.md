# DOC_SYNC_GUIDE.md

## OBJETIVO (documentación viva)
Definir cómo detectar cuando la documentación queda desactualizada con respecto al código. El objetivo es proponer **actualizaciones mínimas** basadas en evidencia, nunca reescribir la documentación completa.

## FUENTES DE VERDAD
Las siguientes fuentes son consideradas fuente de verdad al comparar:

| Fuente | Uso |
|---|---|
| `package.json` | Scripts, `main`, `bin`, `module` |
| `pyproject.toml` | Scripts, entry points |
| `Cargo.toml` | Binarios/targets |
| `go.mod` | Módulo, estructura relevante |
| `pom.xml` | Configuración relevante |
| `src/`, `app/`, `lib/`, `core/`, `api/`, `server/` | Código fuente real |
| `index.*`, `main.*`, `app.*`, `server.*`, `cli.*` | Puntos de entrada |
| `.env.example` | Variables de entorno documentadas |

## QUÉ COMPARAR
| Comparación | Acción |
|---|---|
| **README vs manifiesto** | Comparar scripts listados vs `scripts.*` en `package.json`/`Makefile`/`pyproject.toml`. Detectar scripts faltantes o inexistentes |
| **ARCHITECTURE vs entry point** | Verificar que el punto de entrada mencionado existe (`main`/archivos raíz). Verificar rutas de módulos |
| **Rutas mencionadas** | Comprobar con `glob`/`read` que toda ruta mencionada existe |
| **Comandos** | Verificar que comandos existen en manifiesto |
| **Variables** | Comparar variables mencionadas vs código o `.env.example` |

## USO DE GIT (opcional)
Si existe `.git/`, usarlo para enfocar el análisis:

| Comando | Uso |
|---|---|
| `git diff --name-only` | Archivos modificados recientemente |
| `git log -1 --oneline` | Contexto del último cambio |
| `git diff HEAD~1 HEAD --name-only` | Cambios entre commits (si aplica) |

**Regla:** Si no existe `.git/` o no hay historial, **ignorar** esta sección. Nunca fallar por falta de git.

## HEURÍSTICAS (rutas rotas, scripts inexistentes)
| Heurística | Detección | Acción |
|---|---|---|
| **Ruta rota** | Ruta mencionada no existe con `glob`/`read` | Marcar como `ROTO`. Proponer corregir o eliminar referencia |
| **Script inexistente** | Comando mencionado no existe en manifiesto | Marcar como `DESACTUALIZADO`. Proponer corregir con script real o eliminar |
| **Entry point incorrecto** | ARCHITECTURE menciona entry point distinto al real | Marcar como `DESACTUALIZADO`. Proponer actualizar con evidencia |
| **Módulo inexistente** | Módulo listado no existe | Marcar como `ROTO`. Proponer eliminar o corregir |
| **Variable faltante** | Variable mencionada sin referencia en código/.env.example | Marcar como `DESACTUALIZADO`. Solo proponer si hay evidencia |

## REPORTE DE DESINCRONIZACIÓN (formato)
Generar un reporte claro con este formato:

```markdown
# REPORTE DE DESINCRONIZACIÓN

## Resumen
- Archivos revisados: [...]
- Hallazgos: [X]

## Hallazgos
| Archivo | Tipo | Hallazgo | Evidencia | Propuesta (mínima) |
|---|---|---|---|---|
| README.md | DESACTUALIZADO | Script `dev` listado pero no existe | package.json no tiene script dev | Eliminar o reemplazar con script real |
| ARCHITECTURE.md | ROTO | Ruta `src/old.js` mencionada | glob no encuentra archivo | Eliminar referencia o actualizar ruta |

## Acción recomendada
[Propuesta mínima, basada en evidencia. NO reescribir archivo completo]
```

## REGLAS
- **Solo evidencia** - Cada hallazgo debe tener evidencia verificable con `glob`/`grep`/`read`
- **Mínimo** - Proponer el cambio más pequeño posible. Nunca reescribir todo el archivo
- **Sin inventar** - No inventar scripts/rutas/variables
- **Opcional con git** - Usar git solo si existe, nunca obligatorio
- **Pragmático** - Si no hay hallazgos, reportar "Sin desincronización detectada"
- **Verificable** - Toda propuesta debe poder aplicarse con evidencia
- **Coherente** - Seguir `VALIDATION_CHECKLIST.md` al proponer cambios
