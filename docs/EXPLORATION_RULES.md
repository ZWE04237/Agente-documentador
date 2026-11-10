# EXPLORATION_RULES.md

## OBJETIVO
Definir reglas claras para descubrir, filtrar e ignorar archivos al documentar cualquier repositorio. Minimizar ruido, priorizar lo relevante y delegar correctamente con OpenCode.

## IGNORE-LIST
Ignorar por defecto estos elementos (salvo que sean explícitamente necesarios para entender el proyecto):

| Elemento | Razón |
|---|---|
| `node_modules/` | Dependencias externas |
| `.git/` | Historial VCS |
| `dist/` | Build artefactos |
| `build/` | Build artefactos |
| `out/` | Build artefactos |
| `.next/` | Next.js build/cache |
| `coverage/` | Reportes de cobertura |
| `__pycache__/` | Python cache |
| `.venv/` | Entornos virtuales |
| `venv/` | Entornos virtuales |
| `.idea/` | IDE |
| `.vscode/` | IDE |
| `*.log` | Logs |
| `*.lock` | Lockfiles (solo leer manifiesto si necesario, no indexar) |

## ARCHIVOS PRIORITARIOS
Estos archivos son los primeros a leer para entender el proyecto:

| Archivo | Propósito |
|---|---|
| `README*` | Descripción, uso, instalación |
| `package.json` | Scripts, dependencias, entry points (Node) |
| `pyproject.toml` | Configuración/proyecto Python |
| `Cargo.toml` | Rust |
| `go.mod` | Go |
| `pom.xml` | Java/Maven |
| `tsconfig.json` | TypeScript config |
| `next.config.*` | Next.js |
| `vite.config.*` | Vite |
| `Dockerfile` | Contenedores |
| `docker-compose*` | Orquestación |
| `Makefile` | Scripts/targets |

## DIRECTORIOS RELEVANTES
Priorizar estos directorios al explorar código fuente:

| Directorio | Propósito |
|---|---|
| `src/` | Código fuente principal |
| `app/` | App Router / aplicación |
| `lib/` | Librerías/módulos compartidos |
| `packages/` | Monorepo |
| `core/` | Núcleo/lógica central |
| `api/` | API routes/endpoints |
| `server/` | Servidor/backend |

## CUÁNDO DELEGAR A subagent(explore)
Delegar a `subagent` con `agent: "explore"` cuando:

- **>15 archivos potencialmente relevantes** - Demasiados para leer uno a uno
- **Múltiples directorios** - Necesitas mapa transversal
- **Estructura desconocida y amplia** - Primero obtener un overview
- **Necesitas filtrar rápido** - Obtener listado relevante antes de leer concreto

**Regla:** Tras recibir el resultado, **tú** decides qué archivos leer con `read`. No delegues la redacción o validación.

## HEURÍSTICAS DE RELEVANCIA
Usar estas heurísticas para filtrar:

| Heurística | Acción |
|---|---|
| **Entry points** | Buscar `index.*`, `main.*`, `app.*`, `server.*` y scripts en manifiestos |
| **Imports/Exports** | Usar `grep` para trazar dependencias entre módulos |
| **Configuración** | Leer configs relevantes solo si afectan arquitectura/uso |
| **Tests** | Útiles para entender uso, pero no prioritarios para arquitectura base |
| **Tipos/Interfaces** | Útiles para comprensión, leer solo si necesario |

## REGLA: EVIDENCIA SOBRE SUPOSICIÓN
- **SIEMPRE** verifica con `glob`/`grep`/`read` antes de afirmar.
- **NUNCA** ignores archivos clave solo por la ignore-list si son necesarios para entender el proyecto.
- **Distingue** hecho (verificado) vs inferido (mínimo y justificado).
- **Filtra por relevancia**, no por cantidad. Mejor 5 archivos clave que 50 irrelevantes.
- **Delegación inteligente**: usa `subagent(explore)` para descubrimiento masivo, mantén análisis/síntesis/redacción/validación contigo.
