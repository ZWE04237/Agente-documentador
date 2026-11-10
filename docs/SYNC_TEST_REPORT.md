# REPORTE DE DESINCRONIZACIÓN - TEST SYNC CHECK

## Resumen
- Archivos revisados: `test-sync/sample/package.json`, `test-sync/sample/README.md`
- Hallazgos: 1
- Estado: DESINCRONIZACIÓN DETECTADA
- Fixture temporal eliminado al cerrar la prueba (ver reproducción al final).

## Hallazgos
| Archivo | Tipo | Hallazgo | Evidencia | Propuesta (mínima) |
|---|---|---|---|---|
| README.md | DESACTUALIZADO | Script `dev` existe en manifiesto pero no está documentado | `test-sync/sample/package.json` tiene `"dev": "node index.js"` pero `test-sync/sample/README.md` solo menciona `npm start` | Añadir sección o mención de `npm run dev` en README.md (propuesta mínima) |

## Acción recomendada
Añadir únicamente la referencia al script `dev` existente. No reescribir el README completo. Ejemplo mínimo:

```markdown
## Usage
npm start
npm run dev
```

## Validación
- [x] Basado en evidencia (comparado con package.json real)
- [x] Propuesta mínima (sin reescritura completa)
- [x] Sin inventar scripts
- [x] Sigue `docs/DOC_SYNC_GUIDE.md`

## Reproducción del fixture
El directorio `test-sync/` se eliminó tras la prueba. Para repetirla, crea:

```json
{
  "name": "sync-sample",
  "scripts": {
    "start": "node index.js",
    "dev": "node index.js"
  }
}
```

Y un `README.md` que solo documente `npm start`. El sync check debe detectar `dev` como no documentado.
