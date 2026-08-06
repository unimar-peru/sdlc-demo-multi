# MADUREZ.md — sdlc-demo-multi

> **Estado:** Activo | **Propietario:** Unimar S.A. | **Regla:** S-19
> **Arquitectónica:** 1.0 / 5.0 · **SDLC:** 1.0 / 5.0 · **Global:** 1.0 / 5.0 — Inicial (Ad-Hoc)

Medición de madurez de este satélite, en la escala TOGAF ACMM heredada de [unimar_arch](https://github.com/unimar-peru/unimar_arch). Se valida y repuntúa en cada commit. El validador lo provee el plugin `unimar-core`:

```bash
UNIMAR_CORE=$(ls -d "$HOME"/.claude/plugins/cache/unimar/unimar-core/*/ | sort -V | tail -1)
node "$UNIMAR_CORE/scripts/validate-madurez.mjs" --fix
node "$UNIMAR_CORE/scripts/validate-madurez.mjs" --render
```

Un nivel ≥ 2 exige evidencia enlazada. Un nivel < 5 exige declarar el camino al siguiente. Cada casilla por debajo de 5 tiene su gap en [GAPS.md](./GAPS.md), en la dimensión homónima — y eso no es una buena intención: lo comprueba `validate-correspondencia.mjs`, y falla si alguna casilla se queda sin gap.

La columna **`Dim.`** es el token con el que cada casilla se enlaza a sus gaps. De ella deriva `validate-gaps.mjs` las dimensiones válidas: añadir un pilar o una fase aquí lo reconoce el validador sin tocar código.

> **Un repositorio nuevo empieza abajo.** Un 1.0 no es un fracaso: es el punto de partida honesto. Inflarlo es exactamente lo que SD-05 prohíbe. La evidencia precede a la afirmación.

## 1. Madurez Arquitectónica — Pilares Well-Architected

| Pilar | Nivel | Evidencia | Camino al siguiente nivel | Dim. |
| :--- | ---: | :--- | :--- | :--- |
| Seguridad y Cumplimiento | 1 | — | Cablear los gates locales de S-23 (secretos, auditoría de dependencias) en el pre-commit y enlazar una ejecución como evidencia | `Arq-Seguridad` |
| Eficiencia de Rendimiento | 1 | — | Declarar objetivos de rendimiento por sistema en el blueprint de Fase 2 y enlazar una primera medición | `Arq-Rendimiento` |
| Confiabilidad y Resiliencia | 1 | — | Declarar los SLO de cada sistema y enlazar el primer reporte resumen de pruebas de Fase 4 | `Arq-Confiabilidad` |
| Excelencia Operacional | 1 | — | Dejar el workflow de gobernanza verde en `main` y materializar `_bmad/`, enlazando ambas ejecuciones | `Arq-Operacion` |
| Mantenibilidad y Extensibilidad | 1 | — | Publicar el blueprint de cada sistema con su contexto acotado y enlazarlo desde el hub de Fase 2 | `Arq-Mantenibilidad` |

## 2. Madurez SDLC — Adopción por Fase

| Fase | Nivel | Evidencia | Camino al siguiente nivel | Dim. |
| :--- | ---: | :--- | :--- | :--- |
| 1. Concepción y Descubrimiento | 1 | — | Redactar la carta fundacional `PRD-MPS-001` y los PRD locales de DEMO1 y DEMO2 sobre los borradores que dejó el alta | `SDLC-Concepcion` |
| 2. Diseño y Arquitectura | 1 | — | Redactar los blueprints y las historias funcionales de Fase 2 y trazarlos a ADRs aceptados de `unimar_arch` | `SDLC-Diseno` |
| 3. Construcción | 1 | — | Publicar el primer servicio bajo `src/services/` con su build y sus pruebas reales, y enlazarlas | `SDLC-Construccion` |
| 4. Validación y QA | 1 | — | Ejecutar la primera batería de pruebas y publicar el reporte resumen de Fase 4 con su evidencia | `SDLC-Validacion` |
| 5. Entrega y Operaciones | 1 | — | Publicar las primeras notas de lanzamiento y el índice de iniciativas `reporting/data/initiatives-index.json` (S-25) | `SDLC-Entrega` |

---

<p align="center">
  <strong>© Unimar S.A.</strong> · RUC 20100412447 · Operador Logístico Aduanero desde 1978
</p>
