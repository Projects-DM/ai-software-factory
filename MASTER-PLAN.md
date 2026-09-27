# MASTER-PLAN — AI Software Factory — Dirección global versionada

Estado: dirección global CONCEPTUAL y versionada. No implementa
capacidades. Ninguna fase descrita aquí más allá de F0 debe leerse como
implementada: el roadmap es evolución progresiva condicionada a
evidencia, no funcionalidades existentes.

Este documento es la dirección global del proyecto. El detalle vive en
`docs/`: fundaciones (`01-foundations/`, F0-S1–S3), arquitectura
(`02-architecture/`, F0-S4), workflow (`03-workflow/`, F0-S5), tooling
(`04-tools/`, F0-S6), decisiones (`05-decisions/`, F0-S7) y validación
(`00-governance/`, F0-S8–S9).

## 1. Identidad

AI Software Factory es el sistema / proceso / instrumentación para
construir software de forma asistida y progresivamente automatizada
mediante IA, GitHub, OpenCode, agentes, Rules, Skills, herramientas,
testing, CI/CD, observabilidad, orquestación y supervisión humana. No
es una aplicación de negocio. SGC-DM es referencia externa de
aprendizaje, no parte de la Factory.

## 2. Propósito

Pasar de la coordinación manual entre humano, IA, herramientas, código,
pruebas, documentación y Git a un sistema donde el trabajo se
representa, contextualiza, ejecuta, valida, evidencia y traza de forma
estructurada (F0-S1).

## 3. North Star

> **Construir un sistema de ingeniería de software progresivamente autónomo, verificable y trazable que permita al desarrollador entregar soluciones de calidad con menos trabajo manual, manteniendo control humano, capacidad de recuperación y mejora continua.**

## 4. Objetivos

Dirección F0-S2: menos trabajo manual sobre trabajo comparable
(hipótesis aspiracional 20×–30×, no demostrada, medición F10/F11);
verificabilidad, trazabilidad, autonomía condicionada a evidencia,
recuperación, conocimiento reutilizable justificado y aprendizaje del
desarrollador. Velocidad con degradación de calidad no es mejora.

## 5. Principios

P01–P30 (`docs/01-foundations/PRINCIPLES.md`), con cadena
PRINCIPIO→RULE→SKILL→AGENT y jerarquía NORTH STAR→…→EVOLUTION. Los
principios orientan; las Rules operativas llegan en F1.

## 6. Fases F0–F11

```text
F0 — Fundaciones (identidad → gobernanza; CERTIFIED al cierre F0-S9)
F1 — Rules (principios → reglas operativas)
F2 — Skills (procedimientos reutilizables validados)
F3 — Agents (responsabilidades ejecutoras acotadas)
F4 — Execution / Integration (ejecución controlada; incluye la profundidad Git/GitHub diferida en F0-S6)
F5 — Validation / Quality (validación estructurada y calidad)
F6 — Orchestration (coordinación; coordina, no sustituye)
F7 — Observability / Traceability (evidencia continua y traza operativa)
F8 — Recovery / Resilience (recuperación + auditoría de ejecuciones)
F9 — Controlled Autonomy (autonomía condicionada por evidencia)
F10 — Pilot / Product Validation (piloto independiente de SGC-DM + primera evidencia formal)
F11 — Measurement / Evolution (métricas definitivas y mejora continua)
```

Nomenclatura contrastada con F0-S1–S7: F1 Rules, F2/F3 Agents y Skills,
F4 profundidad Git/integración, F6 orquestación, F7 observabilidad/
trazabilidad, F8 auditoría/recuperación, F9 autonomía condicionada,
F10 piloto, F11 medición/evolución. Sin contradicciones.

## 7. Relación entre fases y roadmap conceptual

```text
F0 Fundaciones (CERRADA al certificarse)
→ F1–F3 instrumentos (Rules, Skills, Agents)
→ F4–F6 ejecución y coordinación
→ F7–F8 observabilidad y recuperación
→ F9 autonomía condicionada
→ F10 validación con piloto
→ F11 medición y evolución
```

Cada fase exige la anterior como entrada y se autoriza con evidencia;
ninguna fase futura está implementada.

## 8. Autonomía progresiva

Nivel 1 Asistencia → Nivel 2 Ejecución supervisada → Nivel 3 Ejecución
autónoma controlada → Nivel 4 Ejecución autónoma condicionada. Modelo
conceptual; ningún nivel declarado alcanzado; `capability ≠ authority`;
Human Gates en bordes de riesgo; P26 rige cada avance.

## 9. Relación Factory / Product

`Factory ≠ Product`: la Factory define cómo se construye; cada Product
define qué se construye con arquitectura y evolución propias. Ningún
Product modifica unilateralmente principios, límites ni arquitectura de
la Factory; los cambios de la Factory siguen su gobernanza (F0-S7).

## 10. Límites de F0

F0 define identidad, objetivos, principios, arquitectura conceptual,
workflow, tooling baseline y gobernanza. No implementa Agents, Skills,
Rules operativas, Orchestrator funcional, CI/CD, observabilidad,
recuperación automatizada ni pilotos. SGC-DM queda fuera.

## 11. Transición F0 → F1

```text
F0 CERTIFIED → F1 UNLOCKED → PRINCIPLES → OPERATIONAL RULES (vía ADR C04 + aprobación humana)
```

F1 dispone de todas sus entradas y no necesita redefinir F0.

## 12. Estado actual y carácter evolutivo

```text
F0 — FUNDACIONES
STATUS: CERTIFIED
NEXT: F1 — RULES
```

La arquitectura es estable pero no definitiva: evoluciona por evidencia
y decisión humana versionada (P20, F0-S7), nunca por auto-modificación.

## 13. Capacidades: actuales, futuras, aspiracionales

- ACTUAL: documentación F0 versionada y gobernada; Git/GitHub/PRs
  manuales; asistencia supervisada.
- FUTURO: F1–F11 por fases con evidencia.
- ASPIRACIONAL: hipótesis 20×–30× (`ASPIRATIONAL ≠ ACHIEVED`).
- Rige siempre: `CAPACIDAD DEFINIDA ≠ CAPACIDAD IMPLEMENTADA ≠
  CAPACIDAD VALIDADA`.
