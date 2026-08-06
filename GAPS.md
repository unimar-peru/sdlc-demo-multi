# GAPS.md — sdlc-demo-multi

> **Estado:** Activo | **Propietario:** Unimar S.A. | **Regla:** S-20
> **Pendientes:** 16 · **En curso:** 0 · **Cerrados:** 3 · **Total:** 19

Registro único de gaps y oportunidades de este satélite. Los contadores de arriba los recalcula el validador; no se editan a mano.

Se ordena y recalcula en cada commit, mediante el validador que provee el plugin `unimar-core`:

```bash
UNIMAR_CORE=$(ls -d "$HOME"/.claude/plugins/cache/unimar/unimar-core/*/ | sort -V | tail -1)
node "$UNIMAR_CORE/scripts/validate-gaps.mjs" --fix
```

## Orden canónico

Los **pendientes van siempre primero**. Después: criticidad, luego complejidad — para que a igual criticidad se ataque antes lo barato.

## Reglas duras

- IDs únicos con formato `G-NNN`.
- La **dimensión** debe ser una casilla de [MADUREZ.md](./MADUREZ.md): el validador las deriva de su columna `Dim.`.
- Un gap **`Cerrado` exige evidencia**: commit, PR o ADR. El validador rechaza un cierre sin respaldo.
- Cada gap declara su **`Apertura`** en formato `AAAA-MM-DD`. Sin fecha no hay antigüedad, y sin antigüedad un gap envejece invisible.
- Cada casilla de madurez con nivel < 5 necesita **al menos un gap en su dimensión**. Lo comprueba `validate-correspondencia.mjs`.

## Registro

| ID | Gap u Oportunidad | Criticidad | Complejidad | Estado | Dimensión | Evidencia | Apertura |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| G-004 | El workflow de gobernanza no se ha ejecutado nunca: el CI está declarado pero sin evidencia de ejecución verde en `main` | Alta | Baja | Pendiente | Arq-Operacion | — | 2026-08-06 |
| G-016 | La plantilla `gobernanza.yml` de `unimar-core@4.4.0` declara dos bloques `env:` en el mismo nivel: la clave duplicada descarta `STANDARD_REF` y el workflow queda sin versión fijada. Persiste en la 4.4.0 (comprobado al actualizar). Corregido en local; propuesta a `unimar_arch` pendiente. Propuesto al núcleo en `unimar_arch#242` | Alta | Baja | Pendiente | Arq-Operacion | — | 2026-08-06 |
| G-001 | Sin postura de seguridad declarada: no hay clasificación de datos, ni superficie de exposición, ni gates de secretos ejecutándose | Alta | Media | Pendiente | Arq-Seguridad | — | 2026-08-06 |
| G-005 | Sin blueprint por sistema: los contextos acotados de DEMO1 y DEMO2 no están delimitados, así que su extensibilidad es una suposición | Alta | Media | Pendiente | Arq-Mantenibilidad | — | 2026-08-06 |
| G-006 | Los artefactos de Fase 1 están en borrador scaffoldeado y sin redactar: no hay PRD de suite ni PRD locales con contenido | Alta | Media | Pendiente | SDLC-Concepcion | — | 2026-08-06 |
| G-007 | Los artefactos de Fase 2 están en borrador y sin trazar a ADRs de `unimar_arch`: el diseño no existe todavía | Alta | Media | Pendiente | SDLC-Diseno | — | 2026-08-06 |
| G-012 | Los gates locales de S-23 (secretos, auditoría de dependencias, cobertura, commitlint) no están cableados en el pre-commit: hoy solo corren los validadores documentales del estándar | Alta | Media | Pendiente | Arq-Seguridad | — | 2026-08-06 |
| G-008 | Sin código ejecutable bajo `src/services/`: la raíz de fuente existe pero no aloja ningún servicio | Alta | Alta | Pendiente | SDLC-Construccion | — | 2026-08-06 |
| G-009 | Sin estrategia de pruebas ni una sola ejecución: Fase 4 no tiene evidencia de ningún tipo | Alta | Alta | Pendiente | SDLC-Validacion | — | 2026-08-06 |
| G-011 | El stack tecnológico autorizado (S-07) se triaja como `Adopt` sin código que lo demuestre. Se comprueba al publicar el primer servicio | Media | Baja | Pendiente | SDLC-Construccion | — | 2026-08-06 |
| G-015 | En `unimar-core@4.4.0` los dos consumidores de `suite.yaml` divergen: `scaffold-artefactos-fase.mjs` solo lee `sistemas` como secuencia en bloque y `validate-suite.mjs` solo como secuencia en flujo. Ninguna forma satisface a ambos; persiste en la 4.4.0. Propuesta a `unimar_arch` pendiente. Propuesto al núcleo en `unimar_arch#245` | Media | Baja | Pendiente | Arq-Mantenibilidad | — | 2026-08-06 |
| G-017 | La plantilla `DECISIONS.md` de `unimar-core@4.4.0` solo trae 23 filas de triaje (S-01…S-23) y su encabezado dice «veintidós», pero `satellite-repo-rules.md` declara 25 reglas: `validate-triaje.mjs` falla en todo satélite recién dado de alta hasta que el operador añade S-24 y S-25 a mano. Persiste en la 4.4.0. Añadidas en local; propuesta a `unimar_arch` pendiente. Propuesto al núcleo en `unimar_arch#243` | Media | Baja | Pendiente | Arq-Mantenibilidad | — | 2026-08-06 |
| G-002 | Sin objetivos de rendimiento por sistema ni una sola medición: la eficiencia no se puede afirmar ni refutar | Media | Media | Pendiente | Arq-Rendimiento | — | 2026-08-06 |
| G-003 | Sin SLO declarados ni estrategia de resiliencia entre DEMO1 y DEMO2: la integración inter-sistema no tiene contrato de disponibilidad | Media | Alta | Pendiente | Arq-Confiabilidad | — | 2026-08-06 |
| G-010 | Sin pipeline de despliegue ni notas de lanzamiento: Fase 5 está declarada pero vacía | Media | Alta | Pendiente | SDLC-Entrega | — | 2026-08-06 |
| G-014 | Las siglas `DEMO1` y `DEMO2` no son `Ratificada` en el catálogo de sistemas: `validate-suite.mjs` las reporta como incumplimiento de su regla 2. Es deliberado (D-003) y acotado a este repositorio de demostración | Baja | Baja | Pendiente | SDLC-Concepcion | — | 2026-08-06 |
| G-013 | `_bmad/` no está materializado (S-17): `npx bmad-method@6.8.0 install --yes --tools claude-code` exige TTY interactivo y no completa en una sesión no interactiva. **Resuelto:** el instalador sí completa sin TTY si se le pasa `--directory <ruta>` — sin ese flag pregunta el directorio y se queda esperando. Instalado con `--directory`, `--communication-language Spanish` y `--document-output-language Spanish` | Media | Baja | Cerrado | Arq-Operacion | 0255eb7 | 2026-08-06 |
| G-018 | El `.gitignore` heredado del repositorio no ignoraba `_bmad/`, `_bmad-output/` ni `.claude/`, así que el árbol que genera el runner de BMAD y la zona protegida del plugin quedaban listos para commitear, contra S-17 y S-21. Se añadió el bloque que trae la plantilla del plugin. | Media | Baja | Cerrado | Arq-Operacion | 0255eb7 | 2026-08-06 |
| G-019 | El hook `commit-msg` no estaba materializado, así que las referencias `G-NNN` y `ADR-NNNN` del mensaje de commit no se comprobaban cuando todavía son corregibles (SD-02). Se materializó desde la plantilla del plugin. | Media | Baja | Cerrado | Arq-Operacion | 0255eb7 | 2026-08-06 |

---

<p align="center">
  <strong>© Unimar S.A.</strong> · RUC 20100412447 · Operador Logístico Aduanero desde 1978
</p>
