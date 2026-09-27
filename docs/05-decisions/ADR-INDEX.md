# ADR-INDEX — AI Software Factory — F0-S7 Índice de decisiones de arquitectura

Fase: F0 — Fundaciones.
Sprint: F0-S7 — Gobernanza y decisiones.
Estado: CONCEPTUAL. Plantilla e índice definidos; sin ADRs reales registrados.

## 1. Propósito

El índice ADR conserva las decisiones importantes de la Factory con su
estado, relaciones e historial. Permite reconstruir por qué el sistema
es como es y qué decisiones lo sostienen.

## 2. Cuándo utilizar ADR

Utilizar ADR para decisiones arquitectónicas (C04), estratégicas (C05)
y fundacionales (C06): elecciones con impacto duradero, alternativas
reales, reversión costosa o riesgo significativo.

No utilizar ADR para decisiones triviales (C01), operativas rutinarias
(C02) ni técnicas menores reversibles (C03): basta registro mínimo
trazado. El criterio es impacto y permanencia, no formato.

## 3. Estructura

Cada ADR contempla: ID, Title, Status, Date, Context, Problem, Options,
Decision, Rationale, Consequences, Risks, Evidence, Review criteria y
Related decisions (plantilla en `ADR-TEMPLATE.md`).

## 4. Estados

`PROPOSED → UNDER REVIEW → ACCEPTED / REJECTED`; tras ACCEPTED, el
ciclo de vida continúa: `IMPLEMENTED → VALIDATED`, o `SUPERSEDED` /
`DEPRECATED` ante decisiones posteriores. Rige `ACCEPTED ≠ IMPLEMENTED`
e `IMPLEMENTED ≠ VALIDATED`: el historial nunca se borra, solo cambia
de estado con justificación.

## 5. Relaciones

Superseding (`ADR-007 supersedes ADR-001`) y deprecation enlazan
decisiones en cadena versionada; cada vínculo conserva qué cambió, por
qué y con qué evidencia. Las decisiones relacionadas se referencian
mutuamente para auditoría.

## 6. Índice actual

En F0-S7 todavía no existen ADRs de producto o arquitectura
registrados: este sprint define el mecanismo, no lo estrena. Las
decisiones fundacionales F0-S1–S7 viven en sus documentos de origen
(`docs/01-foundations/`, `docs/02-architecture/`, `docs/03-workflow/`,
`docs/04-tools/`).

| ID | Title | Status | Date |
|----|-------|--------|------|
| — | (sin registros) | — | — |
