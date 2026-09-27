# AI Software Factory

Sistema profesional de ingeniería de software asistida y progresivamente automatizada mediante IA, GitHub, OpenCode, agentes, Rules, Skills, herramientas, testing, CI/CD, observabilidad y supervisión humana.

```text
F0 — FUNDACIONES
STATUS: CERTIFIED
NEXT: F1 — RULES
```

## Identidad y propósito

La Factory es el sistema / proceso / instrumentación para construir software, no una aplicación de negocio. Existe para sustituir la coordinación manual entre humano, IA, herramientas, código, pruebas, documentación y Git por un proceso estructurado donde el trabajo se representa, ejecuta, valida, evidencia y traza. SGC-DM es solo una referencia externa de aprendizaje, no parte de la Factory (`Factory ≠ Product`).

## North Star

> **Construir un sistema de ingeniería de software progresivamente autónomo, verificable y trazable que permita al desarrollador entregar soluciones de calidad con menos trabajo manual, manteniendo control humano, capacidad de recuperación y mejora continua.**

## Fundaciones (F0 — CERTIFIED)

- Objetivos y North Star: menos trabajo manual con calidad, trazabilidad, control y recuperación; hipótesis aspiracional 20×–30× (no demostrada).
- Principios P01–P30 con cadena PRINCIPIO → RULE → SKILL → AGENT.
- Arquitectura conceptual: 15 componentes C01–C15 con responsabilidades diferenciadas.
- Workflow: lifecycle canónico de 12 estados, excepcionales, Human Gates condicionales y trazabilidad proporcional.
- Tooling baseline mínima y gobernada (Git, GitHub, OpenCode, Markdown, Mermaid); resto FUTURO.
- Gobernanza: autoridad C01–C06, ADR, cambios, excepciones, escalamiento y revisión.

## Estructura y evolución

```text
F0 Fundaciones (CERTIFIED) → F1 Rules → F2 Skills → F3 Agents → F4 Execution/Integration
→ F5 Validation/Quality → F6 Orchestration → F7 Observability/Traceability
→ F8 Recovery/Resilience → F9 Controlled Autonomy → F10 Pilot → F11 Measurement/Evolution
```

Ninguna fase más allá de F0 está implementada. Rige `CAPACIDAD DEFINIDA ≠ IMPLEMENTADA ≠ VALIDADA`.

## Documentación principal

- `MASTER-PLAN.md` — dirección global. `AGENTS.md` — contrato de comportamiento de agentes.
- `docs/01-foundations/` (identidad, objetivos, North Star, principios).
- `docs/02-architecture/` (visión, componentes, diagrama).
- `docs/03-workflow/` (lifecycle, Task, Human Gates, trazabilidad, diagrama).
- `docs/04-tools/` (baseline, selección, OpenCode, GitHub, toolchain).
- `docs/05-decisions/` (gobernanza, ADR, cambios, diagrama).
- `docs/00-governance/F0-VALIDATION-REPORT.md` — evidencia de certificación F0.

Punto de entrada: este README orienta; el detalle vive en los documentos.
