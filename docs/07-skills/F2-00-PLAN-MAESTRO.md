# F2-00 — Plan Maestro de F2 — Skills

- ID: F2-00. Nombre: Plan Maestro de F2 — Skills. Fase: F2 — Skills.
- Tipo: Plan Maestro / Governance / Planning. Estado documental: PLAN MAESTRO / DOCUMENTO DE REFERENCIA DE FASE (no es Skill, sprint funcional, Agent, Runtime, ejecución ni certificación de F2).
- Dependencias: F0 CERTIFIED, F1 CLOSED/CERTIFIED (marco normativo vigente), RUNTIME-DECOUPLING-AUDIT. Relación: F2-S1 → F2-S18.

## 1. Propósito de F2

Construir Skills reutilizables, especializadas, composables, verificables y gobernadas que conviertan capacidades de ingeniería en procedimientos consistentes utilizables por Agents autorizados bajo las Rules de la Factory.

```text
RULES = WHAT IS ALLOWED
SKILLS = HOW A CAPABILITY IS PERFORMED
AGENTS = WHO PERFORMS / COORDINATES RESPONSIBILITY
RUNTIME = WHERE / HOW EXECUTION IS REALIZED
TOOLS = WITH WHAT CAPABILITY IS REALIZED
```

## 2. North Star de F2

Construir Skills reutilizables y verificables que conviertan capacidades de ingeniería en procedimientos consistentes que cualquier Agent autorizado pueda ejecutar bajo Rules, sin dependencia estructural del Agent, Runtime, herramienta o tecnología específica.

## 3. Arquitectura conceptual

```text
FOUNDATIONS = BASE
RULES = WHAT IS ALLOWED
SKILLS = HOW A CAPABILITY IS PERFORMED
AGENTS = WHO PERFORMS / COORDINATES RESPONSIBILITY
RUNTIME = WHERE / HOW EXECUTION IS REALIZED
TOOLS = WITH WHAT CAPABILITY IS REALIZED
```

Preserva: RULE ≠ SKILL, SKILL ≠ AGENT, AGENT ≠ RUNTIME, RUNTIME ≠ TOOL, CAPABILITY ≠ TECHNOLOGY, FACTORY ≠ OPENCODE.

## 4. Decoupling respecto de Runtime

**OpenCode-first, but not OpenCode-dependent.** Factory Rules/Skills/Knowledge → Agent Contract → Agent Selection → Runtime Adapter (no implementado en F2-00) → OpenCode/Runtime B/Runtime C → Tools. OpenCode primer Runtime, no dueño. Coherente con RUNTIME-DECOUPLING-AUDIT (sin desacoplamiento técnico prematuro).

## 5. Capability independence y Database Engineering

`Capability → Skill → Technology` (Database Engineering → Relational Database Engineering → PostgreSQL/MySQL/MariaDB). F2 incluye Database Engineering (modelado, entidades, relaciones, constraints, normalización, índices, schemas, SQL, migrations, seeds, queries, transactions, integración con aplicaciones, repositories/data access, validaciones, integration testing, schema evolution, diagnostics, recovery, documentation). F2-00 solo la planifica; no desarrolla la Skill.

## 6. Roadmap oficial (18 unidades, bloques A–E)

A — Fundaciones: F2-S1 Definition and Skill Contract; F2-S2 Architecture and Organization. B — Capacidades: F2-S3 Analysis; F2-S4 Planning; F2-S5 Architecture; F2-S6 Implementation; F2-S7 Database Engineering; F2-S8 Testing; F2-S9 Code Review; F2-S10 Debugging and Diagnostics. C — Transversales: F2-S11 Documentation; F2-S12 Git/GitHub; F2-S13 Release/Delivery; F2-S14 Technical Research. D — Sistema: F2-S15 Composition; F2-S16 Validation; F2-S17 Governance and Evolution. E — Certificación: F2-S18 Integral Validation. Sin agregados ni eliminaciones.

## 7. Contrato estándar (registro, resultado de F2-S1)

18 campos: ID, Name, Version, Purpose, Capability, Scope, Preconditions, Required Context, Inputs, Procedure, Tools, Outputs, Validation, Evidence, Failure Conditions, Escalation, Related Rules, Changelog. Referencia: `docs/07-skills/F2-S1-SKILL-CONTRACT.md` (sin duplicar su contenido).

## 8. Composición, independencia, alcance y límites

Composición conceptual: Analysis → Requirements Discovery → Planning → Architecture → Database Engineering → Implementation → Testing → Code Review → Git/GitHub → CI/CD → Release → Observability → Validation (sin implementar). Independencia de Agent: ninguna Skill pertenece estructuralmente a un Agent (capacidad, contexto, herramientas, autorización y alcance bastan). Alcance F2: definición, arquitectura, capacidades, composición, validación, gobernanza, evolución, preparación para Agents. Fuera de alcance: Agents definitivos, Orchestrator, autorización automática, autonomía completa, supervisión remota, Runtime Adapter, CI/CD completo, observabilidad completa, infra innecesaria, producción, redefinición de F1.

## 9. Gates, certificación y F3

Gates: 1 aprobación F2-00; 2 arquitectura/contrato pre-creación masiva; 3 revisión individual proporcional; 4 composición; 5 gobernanza; 6 certificación final. Certificación F2: Skills definidas, contratos completos, arquitectura validada, procedimientos verificables, DB cubierta, composición validada, independencias, separación tecnológica, evidencia, gobernanza, compatibilidad F1, preparación F3, 0 blockers, validación integral PASS, certificación humana. F3 LOCKED hasta F2 VALIDATED + evidencia + certificación humana + integración Git + verificación (esta tarea no lo desbloquea).
