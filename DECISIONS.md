# DECISIONS.md — sdlc-demo-multi

> **Estado:** Activo | **Propietario:** Unimar S.A. | **Reglas:** S-15, R-21
> **Tipo de repositorio:** producto

Decisiones locales de este satélite y **triaje de las veinticinco reglas de herencia** (S-01 … S-25). Una decisión local nunca contradice un ADR de `unimar_arch`.

El **tipo de repositorio** (ADR-0069) es `producto` o `libreria`. El defecto es `producto`; cámbielo a `libreria` si este satélite publica un paquete que otros consumen en vez de un sistema que se despliega. El tipo condiciona las ramas (ADR-0050), los artefactos SDLC (S-01 … S-05), el README y la lectura de la madurez. Un satélite `libreria` triaja S-01 … S-05 como `N/A` por su tipo.

## Operaciones

| Operación | Significado |
| :--- | :--- |
| `Adopt` | Se toma la regla tal cual, sin modificaciones. |
| `Extend` | Se toma y se añaden extensiones locales que no la contradicen. |
| `Override` | Se reemplaza localmente. Solo donde está permitido, y **exige ADR local** que lo justifique. |
| `N/A` | No aplica por contexto. **Se declara por qué**, no se deja en blanco. |

> `N/A` por decisión y `N/A` por ausencia no son lo mismo. Si la regla no se cumple porque el artefacto todavía no existe, eso es un **gap**, no una exención: regístrelo en [GAPS.md](./GAPS.md).

## Triaje de las reglas de herencia

| Regla | Operación | Justificación |
| :--- | :--- | :--- |
| S-01 Plantillas Base | Adopt | Los artefactos SDLC se instancian desde el Hub de Plantillas del plugin. El alta los pre-creó en borrador con `scaffold-artefactos-fase.mjs` (ADR-0149). |
| S-02 Formato Canónico | Adopt | Encabezado de estado, propietario y regla en todo artefacto normativo; lo comprueba `validate-docs.mjs`. |
| S-03 Diagramas Mermaid | Adopt | Todo diagrama va en Mermaid embebido, sin imágenes binarias. |
| S-04 Requisitos Técnicos Aislados | Adopt | Los requisitos técnicos viven en su sección aislada del artefacto, no mezclados con los funcionales. |
| S-05 Actores y Stakeholders | Adopt | Cada artefacto de Fase 1 y 2 declara actores y stakeholders con nombre. |
| S-06 Trazabilidad a ADRs | Adopt | Toda decisión técnica referencia un ADR aceptado de `unimar_arch`; si no existe, se crea allí primero. |
| S-07 Stack Tecnológico Autorizado | Adopt | El stack de `reference/architecture/stack-tecnologico-autorizado-agnostico.es.md` rige los servicios de `src/services/`. Todavía sin código: ver [G-011](./GAPS.md). |
| S-08 Versión SemVer en Plantillas | Adopt | Cada artefacto instanciado conserva y versiona en SemVer la plantilla de la que deriva. |
| S-09 Idioma Único | Adopt | Español, sin pares bilingües ni archivos `.en.md` (SD-08). |
| S-10 Referencias Relativas | Adopt | Enlaces relativos desde la ubicación del archivo; un enlace roto falla la tarea (SD-06). |
| S-11 Badges Uniformados | Adopt | El [README.md](./README.md) usa el juego de badges de la plantilla `README.multi-product.md` del plugin. |
| S-12 Validación Pre-Commit | Adopt | [`.husky/pre-commit`](.husky/pre-commit) encadena los validadores del plugin; el CI los repite en [`gobernanza.yml`](.github/workflows/gobernanza.yml). |
| S-13 Historial de Cambios | Adopt | Todo artefacto normativo cierra con su tabla de historial de cambios. |
| S-14 Guía de Estilo | Adopt | La guía de estilo documental del núcleo, sin variante local. |
| S-15 Decisiones Locales | Adopt | Este archivo es el registro. |
| S-16 Estándar Provisto, no Copiado | Adopt | El estándar lo provee el plugin `unimar-core`. Este repositorio no contiene `.harness/`. La versión se fija en `STANDARD_REF`. |
| S-17 Agentes BMAD | Adopt | Se adopta la versión `6.8.0` que fija el manifiesto de `unimar_arch`. `_bmad/` está materializado; el runner elegido se declara en [D-006](#decisiones-locales). Lo que se hereda es la versión, no los archivos que genera el runner: `_bmad/` no se commitea ([G-018](./GAPS.md)). |
| S-18 Taxonomía y Configuración Base | Adopt | Raíz de fuente `src/` (ADR-0107) y esqueleto de la taxonomía materializados. El perfil **`multi-product`** abre el segundo nivel por alcance dentro de cada fase (`suite/`, `DEMO1/`, `DEMO2/`) — eso es la taxonomía §2.3, no una extensión local. |
| S-19 Medición de Madurez | Adopt | [MADUREZ.md](./MADUREZ.md) |
| S-20 Registro Único de Gaps | Adopt | [GAPS.md](./GAPS.md) |
| S-21 Rulesets de Agentes | Adopt | Los subagentes los provee el plugin. `.claude/agents/` es zona protegida. |
| S-22 Reglas Spec-Driven | Adopt | SD-01 … SD-08 se acatan tal cual: la especificación precede al código y la evidencia a la afirmación. |
| S-23 Gates de Calidad y Seguridad Local-First | Adopt | El pre-commit ya encadena los validadores del estándar. Los gates de secretos, dependencias y cobertura se cablean con el primer runtime en `src/`. Ver [G-012](./GAPS.md). |
| S-24 Fase 1 Define, el Tablero Planifica | Adopt | Los artefactos de Fase 1 ordenan y estiman; las fechas, la línea base y el avance real son del tablero SDLC. Ninguna carpeta de `docs/01-concepcion/` declara calendario. |
| S-25 Índice de Iniciativas Publicado | Adopt | Se publicará `reporting/data/initiatives-index.json` en cuanto el primer PRD deje el borrador y declare su identificador. Hoy no hay PRD redactado, así que el validador no aplica. Ver [G-010](./GAPS.md). |

## Decisiones locales

| ID | Decisión | Fecha | Justificación |
| :--- | :--- | :--- | :--- |
| D-001 | Perfil **`multi-product`**: este satélite aloja una Suite con varios sistemas, no un producto único. | 2026-08-06 | Es el objeto del repositorio: demostrar el SDLC Unimar sobre una suite multiproducto. Se declara en [`suite.yaml`](./suite.yaml) y un [`sistema.yaml`](src/services/DEMO1/sistema.yaml) por sistema, conforme a ADR-0120 §2.5. |
| D-002 | La Suite se identifica **`MPS`** — _Multi-Product Sample_. | 2026-08-06 | `MPS` no colisiona con ninguna sigla del [catálogo de sistemas](https://github.com/unimar-peru/unimar_arch/blob/main/reference/architecture/catalogo-sistemas-suite.es.md) y sigue el patrón `?MS` de su regla 6. Se descartó `MMS`, que ya designa el Sistema de Data Maestra: reasignarla reproduciría la colisión que su regla 3 prohíbe y que originó G-080. |
| D-003 | Los sistemas de la Suite son **`DEMO1`** y **`DEMO2`**, siglas **no ratificadas** y de uso exclusivamente demostrativo. | 2026-08-06 | Este repositorio no construye ningún sistema real de la suite Unimar: es material de demostración del SDLC. Usar siglas ficticias evita que un artefacto de demo se confunda con uno normativo de `DT`, `TMS` o `UMS`. La contrapartida —`validate-suite.mjs` las reporta como no `Ratificada`— se declara y se registra en [G-014](./GAPS.md), no se disimula. |
| D-004 | `suite.yaml` declara `sistemas` como **secuencia en bloque** YAML, no en flujo. | 2026-08-06 | Los dos consumidores del archivo divergen en el plugin `unimar-core@4.4.0`: `scaffold-artefactos-fase.mjs` solo reconoce la forma en bloque y `validate-suite.mjs` solo la forma en flujo del ejemplo de ADR-0120 §2.5. Se prioriza la que materializa el árbol documental; el aviso residual del validador se registra en [G-015](./GAPS.md) y se propone aguas arriba. |
| D-005 | `STANDARD_REF` se fija en **`unimar-core-4.4.0`**. | 2026-08-06 | Es la versión del plugin instalada y adoptada en el alta. Apuntar a `main` renunciaría a builds reproducibles. |
| D-006 | Runner de BMAD: **`claude-code`**, instalado con `npx bmad-method@6.8.0 install --yes --tools claude-code --directory <ruta>`. | 2026-08-06 | S-17 hereda la **versión** de `unimar_arch`, no los archivos que genera el runner; el runner se declara aquí. El flag `--directory` es lo que hace la instalación no interactiva: sin él, `--yes` no cubre la pregunta por el directorio y el instalador se queda esperando, que fue lo que se leyó como «exige TTY» en [G-013](./GAPS.md). |

---

<p align="center">
  <strong>© Unimar S.A.</strong> · RUC 20100412447 · Operador Logístico Aduanero desde 1978
</p>
