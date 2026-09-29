# F1-S2-VALIDATION — Matriz de aceptación RC-01

Fase: F1 — Rules. Sprint: F1-S2. Resultados: PASS / BLOCKED (sin
CERTIFIED). Todas las Rules en PROPOSED v0.1: definidas ≠ aprobadas ≠
activas.

| ID | Criterion | Evidence | Result | Notes |
|----|-----------|----------|--------|-------|
| A01 | Comprender objetivo | R-GB-001 (verificación previa, MUST/HIGH) | PASS | — |
| A02 | No inventar requisitos | R-GB-002 (MUST/CRITICAL, P06) | PASS | — |
| A03 | Hechos/supuestos/incertidumbre | R-GB-002 (KNOWN/UNCERTAIN/CRITICALLY UNCERTAIN) | PASS | — |
| A04 | Respetar alcance | R-GB-003 (límite = Task+Auth+Rules; MUST/HIGH) | PASS | — |
| A05 | Capability ≠ Authorization | R-GB-004 (MUST NOT/CRITICAL) + 4 niveles §5 F1-S2 | PASS | — |
| A06 | Responsabilidad | R-GB-004 (P10, no sustituir Orchestrator) | PASS | — |
| A07 | Integridad del trabajo | R-GB-005 (P05, impacto previo; MUST/HIGH) | PASS | Detalle archivos → F1-S4 |
| A08 | Validación antes de éxito | R-GB-006 (cadena + MUST/CRITICAL, sin autocertificación) | PASS | Detalle testing → F1-S5 |
| A09 | Transparencia de errores | R-GB-007 (MUST/HIGH, 6 supuestos) | PASS | Recovery → F1-S8 |
| A10 | Detención segura | R-GB-008 (7 condiciones, STOP válido, estados F0-S5) | PASS | — |
| A11 | Escalamiento | R-GB-009 (7 elementos, PROPOSE≠DECIDE, sin autorización por silencio) | PASS | Gates → F1-S9 |
| A12 | Evidencia | R-GB-010 (WHAT…SOURCE, proporcional al riesgo) | PASS | Detalle → F1-S10 |
| A13 | Trazabilidad | R-GB-010 (cadena Task→Decision) | PASS | Detalle → F1-S10 |
| A14 | Precedencia de Rules | R-GB-011 (MUST/CRITICAL, §§2–3 gobernanza) | PASS | — |
| A15 | Prohibiciones universales | R-GB-002/003/004/006/007/011 (11 conductas §18 cubiertas) | PASS | Técnicas → sus categorías |
| A16 | Coherencia AGENTS.md | Formalización 1:1 sin reemplazo (cadena Human→Traceability preservada) | PASS | Sin contradicciones |
| A17 | Coherencia F0 | P02/P03/P05/P06/P09/P10/P13/P14/P26/P29 + lifecycle + gates + C01–C06 | PASS | F0 intacto |
| A18 | Coherencia F1-S1 | 20 campos por Rule; estados PROPOSED; RC-01 sin invadir RC-02…11 | PASS | Contrato utilizable: PASS |
| A19 | Independencia herramientas | Alcance genérico; 0 menciones de herramienta concreta | PASS | — |
| A20 | Independencia agentes | Sin rol/implementación específica; C-niveles, no nombres | PASS | — |
| A21 | Ausencia scope creep | Sin Agents/Skills/Orchestrator/enforcement; dependencias documentadas (testing→S5, recovery→S8, gates→S9, traza→S10, archivos→S4) | PASS | — |

## Pregunta principal

> ¿Establecen un comportamiento mínimo común, concreto y verificable
> para cualquier agente futuro, sin depender de especialidad,
> herramienta o implementación, y sin contradecir F0 ni F1-S1?

SÍ. 11 Rules verificables (condición + acción/restricción + evidencia
cada una), independientes de implementación (A19/A20), coherentes con
F0 (A17) y F1-S1 (A18), con dependencias futuras documentadas en vez
de implementadas (A21). 0 BLOCKED.
