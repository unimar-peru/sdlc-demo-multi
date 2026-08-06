# sdlc-demo-multi

<div align="center">

![Unimar](https://img.shields.io/badge/Unimar_Arch-003c6b?style=for-the-badge)
![Perfil](https://img.shields.io/badge/Perfil-multi--product-8e44ad?style=for-the-badge)
![Suite](https://img.shields.io/badge/Suite-MPS-0f3e67?style=for-the-badge)
![Estado](https://img.shields.io/badge/Estado-Activo-27ae60?style=for-the-badge)
![Satélite](https://img.shields.io/badge/Sat%C3%A9lite-S--16-042139?style=for-the-badge)
![License](https://img.shields.io/badge/License-MIT-informational?style=for-the-badge)

<br/>

**Repositorio de demostración del SDLC Unimar sobre una suite multiproducto.**<br/>
Satélite de [`unimar_arch`](https://github.com/unimar-peru/unimar_arch): consume el estándar corporativo, versionado, desde el plugin `unimar-core`. No lo copia.

> _Operador Logístico Aduanero desde 1978_

</div>

**MPS — Multi-Product Sample** es una Suite de demostración: dos sistemas que evolucionan de forma independiente y se consolidan en una visión integrada, para ejercitar el ciclo completo Suite → Sistema → PRD sin tocar ningún sistema real de la suite Unimar. La carta fundacional es [`PRD-MPS-001`](docs/01-concepcion/suite/prd-mps-001.es.md) (`Alcance: suite`).

| Identidad | |
| :--- | :--- |
| Tipo de repositorio (ADR-0069) | `producto` |
| Perfil | `multi-product` |
| Suite | **MPS** — Multi-Product Sample |
| Productos | DEMO1 · DEMO2 — **siglas ficticias, no `Ratificada`** ([D-003](DECISIONS.md), [G-014](GAPS.md)) |
| Raíz de fuente (ADR-0107) | `src/` |
| Owner | Architecture Board |

> **Este repositorio es material de demostración.** Sus dos sistemas no existen en el [catálogo de sistemas de la suite](https://github.com/unimar-peru/unimar_arch/blob/main/reference/architecture/catalogo-sistemas-suite.es.md), y eso es deliberado: usar `DT` o `TMS` aquí haría que un artefacto de demo se pudiera confundir con uno normativo. `validate-suite.mjs` reporta las siglas como no ratificadas; el aviso es esperado y está registrado.

---

## Flujo SDLC

Abre la fase en la que trabajas. Cada una declara su **meta**, sus documentos y sus **hubs** (índices de área), de nivel Suite y por sistema.

> **Numeración canon `unimar_arch`:** las fases van de **1 a 5** (Mapeo SDLC–Artefactos). **No existe «Fase 0».** Cada sistema evoluciona con su propio ritmo; esta vista consolida.
>
> Todos los artefactos de abajo están **en borrador**: los pre-creó el alta del satélite desde su plantilla canónica ([ADR-0149](https://github.com/unimar-peru/unimar_arch/blob/main/reference/architecture/adrs/core/0149-scaffolding-artefactos-alta-satelite.es.md)). Redactarlos es el trabajo pendiente ([G-006](GAPS.md), [G-007](GAPS.md)).

<details>
<summary><strong>Fase 1 — Concepción y Descubrimiento</strong> · visión y requisitos</summary>

<br/>

> **Meta:** fijar el _qué_ y el _para quién_ de la Suite y de cada sistema.

| Documento | Descripción | Tipo |
| :--- | :--- | :--- |
| [Hub de Fase 1](docs/01-concepcion/README.md) | Consolida el estado de la Suite y de sus dos sistemas | Hub |
| [PRD de Suite](docs/01-concepcion/suite/prd-mps-001.es.md) | Carta fundacional `PRD-MPS-001` (`Alcance: suite`) | PRD |
| [PRD DEMO1](docs/01-concepcion/DEMO1/prd-demo1-001.es.md) · [PRD DEMO2](docs/01-concepcion/DEMO2/prd-demo2-001.es.md) | `PRD-<Sistema>-001` (`Alcance: local`) | PRD |
| [Historias de usuario](docs/01-concepcion/DEMO1/historias-usuario-demo1-001.es.md) · [Backlog ágil](docs/01-concepcion/DEMO1/backlog-agil-demo1-001.es.md) | Por sistema; el hub enlaza también los de DEMO2 | Backlog |

</details>

<details>
<summary><strong>Fase 2 — Diseño y Arquitectura</strong> · topología y contratos</summary>

<br/>

> **Meta:** fijar el _cómo_ estructural; cada sistema es un Bounded Context.

| Documento | Descripción | Tipo |
| :--- | :--- | :--- |
| [Hub de Fase 2](docs/02-diseno/README.md) | Topología de la Suite y contratos entre sistemas | Hub |
| [Blueprint de Suite](docs/02-diseno/suite/blueprint-mps-001.es.md) | Diseño de lo que cruza sistemas | Blueprint |
| [Blueprint DEMO1](docs/02-diseno/DEMO1/blueprint-demo1-001.es.md) · [Blueprint DEMO2](docs/02-diseno/DEMO2/blueprint-demo2-001.es.md) | Diseño de cada Bounded Context | Blueprint |
| [Corpus de ADRs del núcleo](https://github.com/unimar-peru/unimar_arch/tree/main/reference/architecture/adrs) | Toda decisión técnica traza a un ADR **aceptado** de `unimar_arch` (S-06) | Decisión |

</details>

<details>
<summary><strong>Fase 3 — Construcción</strong> · el monorepo gobernado</summary>

<br/>

> **Meta:** materializar el diseño en código gobernado (monorepo).

| Documento | Descripción | Tipo |
| :--- | :--- | :--- |
| [Hub de Fase 3](docs/03-construccion/README.md) | Historias técnicas y planes por sistema | Hub |
| [Historias técnicas DEMO1](docs/03-construccion/DEMO1/historias-tecnicas-demo1-001.es.md) · [DEMO2](docs/03-construccion/DEMO2/historias-tecnicas-demo2-001.es.md) | Trabajo de construcción por sistema | Historia |
| `src/services/DEMO1/` · `src/services/DEMO2/` | Un servicio por sistema. **Todavía sin código** ([G-008](GAPS.md)) | Código |

</details>

<details>
<summary><strong>Fase 4 — Validación y QA</strong> · la promesa se comprueba</summary>

<br/>

> **Meta:** comprobar que cada sistema cumple lo prometido.

| Documento | Descripción | Tipo |
| :--- | :--- | :--- |
| [Hub de Fase 4](docs/04-validacion/README.md) | Planes, cobertura y criterios de salida | Hub |
| [Reporte de pruebas de Suite](docs/04-validacion/suite/reporte-resumen-pruebas-mps-001.es.md) | Evidencia consolidada | Pruebas |
| [Reporte DEMO1](docs/04-validacion/DEMO1/reporte-resumen-pruebas-demo1-001.es.md) · [DEMO2](docs/04-validacion/DEMO2/reporte-resumen-pruebas-demo2-001.es.md) | Evidencia por sistema y capa | Pruebas |

</details>

<details>
<summary><strong>Fase 5 — Entrega y Operaciones</strong> · lo que ya corre</summary>

<br/>

> **Meta:** operar la Suite y sostener su superficie de integración.

| Documento | Descripción | Tipo |
| :--- | :--- | :--- |
| [Hub de Fase 5](docs/05-entrega/README.md) | Runbooks, releases y operación | Hub |
| [Notas de lanzamiento de Suite](docs/05-entrega/suite/notas-lanzamiento-mps-001.es.md) | Release consolidado de la Suite | Runbook |
| [Notas DEMO1](docs/05-entrega/DEMO1/notas-lanzamiento-demo1-001.es.md) · [DEMO2](docs/05-entrega/DEMO2/notas-lanzamiento-demo2-001.es.md) | Versionado por sistema | Runbook |

</details>

---

## Cómo colaborar

<details>
<summary><strong>Arranque rápido</strong> · del clon al primer commit válido</summary>

<br/>

Este repositorio no lleva el estándar dentro. Lo obtiene del plugin `unimar-core`, que se instala una vez y se comparte entre satélites.

1. **Instala el plugin del estándar** (marketplace de Unimar):

   ```bash
   claude plugin marketplace add unimar-peru/unimar-marketplace
   claude plugin install unimar-core@unimar
   ```

2. **Localiza la versión instalada y activa el hook** (una vez por clon; git no lo activa solo, por diseño):

   ```bash
   UNIMAR_CORE=$(ls -d "$HOME"/.claude/plugins/cache/unimar/unimar-core/*/ | sort -V | tail -1)
   node "$UNIMAR_CORE/scripts/install-hooks.mjs"
   ```

3. **Valida la gobernanza** antes de tu primer commit:

   ```bash
   # Con Claude Code, el barrido completo en un paso:
   #   /unimar-core:validar-gobernanza
   node "$UNIMAR_CORE/scripts/validate-estructura-satelite.mjs"
   node "$UNIMAR_CORE/scripts/validate-satellite-base.mjs"
   ```

4. **Build y pruebas.** Este satélite todavía no aloja código ejecutable ([G-008](GAPS.md)); hasta entonces la build es el lint documental y las pruebas, el barrido de ubicación y del modelo Suite → Sistema:

   ```bash
   npx --yes markdownlint-cli@0.39.0 --config .markdownlint.json \
     --ignore .claude --ignore _bmad --ignore _bmad-output --ignore .estandar "**/*.md"
   node "$UNIMAR_CORE/scripts/validate-ubicacion-artefactos.mjs"
   node "$UNIMAR_CORE/scripts/validate-suite.mjs"
   ```

</details>

<details>
<summary><strong>Reglas que gobiernan tu cambio</strong> · gobernanza viva del satélite</summary>

<br/>

| Documento | Qué gobierna |
| :--- | :--- |
| [CLAUDE.md](./CLAUDE.md) | Reglas del núcleo Unimar, redactadas para este satélite |
| [CONTRIBUTING.md](./CONTRIBUTING.md) | Proceso de contribución y cómo proponer cambios al núcleo |
| [AGENTS.md](./AGENTS.md) | Convenciones para agentes que operen aquí |
| [DECISIONS.md](./DECISIONS.md) | Triaje de herencia y decisiones locales |
| [GAPS.md](./GAPS.md) | Registro único de hallazgos (S-20) |
| [MADUREZ.md](./MADUREZ.md) | Medición de madurez TOGAF ACMM (S-19) |

**Quality & Security:** los gates locales (S-23, ADR-0106) todavía no están cableados en este satélite — hoy solo corren los validadores documentales del estándar. Es un hallazgo abierto: [G-012](GAPS.md).

</details>

<details>
<summary><strong>Proponer un cambio al estándar</strong> · el camino de vuelta al núcleo</summary>

<br/>

Lo que este repositorio no puede decidir por su cuenta —una regla, un validador, una plantilla, un ADR de núcleo— se propone en [`unimar_arch`](https://github.com/unimar-peru/unimar_arch) por PR. El estándar baja versionado en el plugin; nunca se parchea en local.

El detalle del flujo, con roles y categorías de cambio, está en [CONTRIBUTING.md](./CONTRIBUTING.md), sección «Contribuir al núcleo». Este satélite ya tiene dos propuestas pendientes de abrir: [G-015](GAPS.md) y [G-016](GAPS.md).

</details>

---

## Preguntas y respuestas

<details>
<summary><strong>¿Qué productos tiene la Suite y dónde vive cada uno?</strong></summary>

<br/>

| Sistema | Qué es | `sistema.yaml` | PRDs | Estado |
| :--- | :--- | :--- | :--- | :--- |
| **DEMO1** — Sistema de Demostración 1 | Sistema ficticio para ejercitar el ciclo Suite → Sistema → PRD | [`src/services/DEMO1/sistema.yaml`](src/services/DEMO1/sistema.yaml) | [`PRD-DEMO1-001`](docs/01-concepcion/DEMO1/prd-demo1-001.es.md) | Fase 1 |
| **DEMO2** — Sistema de Demostración 2 | Segundo sistema ficticio; existe para que la consolidación de Suite tenga algo que consolidar | [`src/services/DEMO2/sistema.yaml`](src/services/DEMO2/sistema.yaml) | [`PRD-DEMO2-001`](docs/01-concepcion/DEMO2/prd-demo2-001.es.md) | Fase 1 |

Un producto es una **capacidad funcional**, no una app: se sirve desde la Web/App compartidas más sus servicios propios.

</details>

<details>
<summary><strong>¿Dónde va cada cosa en este repositorio?</strong></summary>

<br/>

```text
suite.yaml           declaración de la Suite MPS (ADR-0120)
src/                 raíz de fuente (ADR-0107) — todo el código bajo src/
  services/          un Bounded Context por sistema
    DEMO1/           sistema.yaml + código del sistema
    DEMO2/
docs/                artefactos SDLC, particionados por fase y, dentro, por alcance
  01-concepcion/     README.md (hub) · suite/ · DEMO1/ · DEMO2/
  02-diseno/  03-construccion/  04-validacion/  05-entrega/
reference/           corpus propio (ADRs locales, blueprints, deployment)
  governance/gaps/   fichas de detalle y evidencia de los gaps
DECISIONS.md  GAPS.md  MADUREZ.md  CLAUDE.md  CONTRIBUTING.md  AGENTS.md
```

El primer nivel es **la fase**, y el segundo el **alcance** (`suite/` o la sigla del sistema). Se descartó invertirlo: la navegación SDLC del estándar abre por fase, y un satélite que pasa de uno a varios productos solo añade el segundo nivel en vez de migrar todo `docs/`.

Satélites de apoyo — **integración, no pertenencia**: ninguno. Esta Suite es autocontenida por ser demostrativa.

</details>

<details>
<summary><strong>¿Cómo se comunican los sistemas entre sí?</strong></summary>

<br/>

_Patrón normativo del núcleo — no lo redefinas, referéncialo:_

- **Intra-servicio** (entre agregados y contextos de un mismo sistema): **eventos de dominio in-memory** ([ADR-0015](https://github.com/unimar-peru/unimar_arch/blob/main/reference/architecture/adrs/core/0015-arquitectura-eventos-intradominio.es.md)).
- **Persistencia**: **una base de datos por servicio**, esquema por contexto (_database-per-service_, [ADR-0031](https://github.com/unimar-peru/unimar_arch/blob/main/reference/architecture/adrs/core/0031-esquema-por-contexto-catalogo-eventos-dominio.es.md)). Ningún sistema lee la BD de otro.
- **Inter-sistema** (entre sistemas de la Suite): **eventos de integración a través del bróker XMS en coreografía** ([ADR-0097](https://github.com/unimar-peru/unimar_arch/blob/main/reference/architecture/adrs/core/0097-integracion-entre-sistemas-suite-eventos-xms.es.md), en ratificación), con contrato AsyncAPI/CloudEvents, entrega FIFO/DLQ e idempotencia ([ADR-0036](https://github.com/unimar-peru/unimar_arch/blob/main/reference/architecture/adrs/core/0036-estrategia-entrega-bus-mensajes-fifo-dlq.es.md)) y publicación garantizada por _outbox_ ([ADR-0033](https://github.com/unimar-peru/unimar_arch/blob/main/reference/architecture/adrs/core/0033-patron-transactional-outbox.es.md)). El transporte del bus (p. ej. RabbitMQ) no acopla sistemas punto a punto.

Toda integración externa cruza el bróker con contrato declarado.

</details>

<details>
<summary><strong>¿Por qué no hay <code>.harness/</code> aquí?</strong></summary>

<br/>

Porque el satélite **consume** el estándar, no lo aloja (S-16). Reglas, scripts y subagentes llegan por el plugin `unimar-core`, así que todos los satélites ejecutan exactamente la misma versión y esa versión es su identidad ([ADR-0062](https://github.com/unimar-peru/unimar_arch/blob/main/reference/architecture/adrs/core/0062-estandar-distribuido-como-plugin-versionado.es.md)). Un hook `PreToolUse` deniega la escritura en `.harness/` y el CI la rechaza.

</details>

<details>
<summary><strong>¿Cómo actualizo el estándar a una versión nueva?</strong></summary>

<br/>

```bash
claude plugin update unimar-core@unimar
UNIMAR_CORE=$(ls -d "$HOME"/.claude/plugins/cache/unimar/unimar-core/*/ | sort -V | tail -1)
node "$UNIMAR_CORE/scripts/validate-estructura-satelite.mjs"
```

La versión adoptada se fija en `STANDARD_REF` del [workflow de gobernanza](.github/workflows/gobernanza.yml) — hoy `unimar-core-4.4.0`. Si la versión nueva añade reglas, el triaje correspondiente se registra en [DECISIONS.md](./DECISIONS.md) con su operación `Adopt` / `Extend` / `Override` / `N/A`.

</details>

<details>
<summary><strong>El pre-commit me bloqueó. ¿Qué hago?</strong></summary>

<br/>

Léelo: los validadores nombran el archivo y la regla. No se saltan con `--no-verify` — un gate evadido es un gate roto, y el CI lo vuelve a encontrar. Si crees que el validador se equivoca, eso **es** un hallazgo: regístralo en [GAPS.md](./GAPS.md) y propón el arreglo en `unimar_arch`.

</details>

<details>
<summary><strong>Encontré algo que no puedo arreglar ahora. ¿Dónde lo registro?</strong></summary>

<br/>

En [GAPS.md](./GAPS.md), con su dimensión de madurez, criticidad y complejidad (SD-07). Con Claude Code: `/unimar-core:unimar-gap`. La evidencia precede a la afirmación (SD-05): si no puedes enlazar la prueba, el hallazgo se registra como pendiente en vez de darse por resuelto.

</details>

<details>
<summary><strong>Necesito una decisión técnica que no tiene ADR. ¿La decido aquí?</strong></summary>

<br/>

No. Toda decisión técnica referencia un ADR **aceptado** de `unimar_arch`; si no existe, se crea allí primero (S-06). Lo que sí vive aquí son los ADR **locales** (`ADR-<Sistema>-NNN`): decisiones propias de un sistema que no alteran el estándar.

</details>

---

<div align="center">

**© Unimar S.A.** · RUC 20100412447 · Operador Logístico Aduanero desde 1978<br/>
Estándar: [Unimar Arch](https://github.com/unimar-peru/unimar_arch) · Plugin: `unimar-core`

</div>
