# TOOL-SELECTION — AI Software Factory — F0-S6 Criterios de selección

Fase: F0 — Fundaciones.
Sprint: F0-S6 — Herramientas y entorno.
Estado: definición documental y estratégica. No adopta ni implementa herramientas.

Este documento gobierna cómo entra (y sale) cualquier herramienta de la
Factory. La adopción es una decisión gobernada, no acumulativa: la
necesidad justifica la herramienta, nunca al revés.

## 1. Criterios de selección

```text
C01 — Need: responde a una necesidad demostrada del lifecycle o la arquitectura
C02 — Value: aporta beneficio verificable (menos trabajo, menos errores, más calidad, trazabilidad, recuperación, reutilización)
C03 — Compatibility: convive con la baseline y el flujo sin exigir rediseño
C04 — Automation: su grado de automatización es el que la evidencia permite, ni más ni menos
C05 — Security: no amplía superficie de riesgo más allá de lo justificado y gobernado
C06 — Maintainability: su costo de mantenimiento no supera su beneficio (P08)
C07 — Reproducibility: no depende de configuración manual no registrada
C08 — Observability: lo que hace puede observarse y vincularse a evidencia
C09 — Replaceability: puede sustituirse sin reconstruir el sistema (P21)
C10 — Complexity: no introduce complejidad desproporcionada a su valor (P27)
C11 — Cost: coste total (licencias, operación, aprendizaje) conocido y asumible
C12 — Lock-in: el acoplamiento a proveedor es explícito, acotado y reversible
```

No se adopta una herramienta porque sea popular, nueva, completa,
usada en otras arquitecturas, marginalmente útil o usada por otros
proyectos. Sin necesidad (C01) no hay evaluación.

## 2. Proceso de adopción

```text
Need
→ Evaluation (alternativas contra C01–C12)
→ Decision (autorizada según riesgo; decisiones significativas pueden requerir ADR)
→ Adoption (alcance acotado y reversible)
→ Validation (comprobación posterior de valor real)
```

Si la validación posterior no confirma el valor, la adopción se revierte:
automatizar con costo mayor al beneficio se reconsidera (P08).

## 3. Proceso de sustitución

```text
Limitación o necesidad nueva
→ Evaluación de alternativas (mismos criterios C01–C12)
→ Decisión con plan de migración y reversión
→ Sustitución versionada y trazada
→ Validación de equivalencia o mejora (P25)
```

La reemplazabilidad se diseña antes de necesitarse:

```text
INTERFACE / RESPONSIBILITY
        ↓
Tool A / Tool B / Tool C
```

Objetivo: evitar `Tool → define architecture`; favorecer
`Architecture / Responsibility → selects appropriate tool`. No es
implementar soporte multi-tool: es no depender conceptualmente de una
marca cuando la responsabilidad puede definirse independientemente.

## 4. Decisiones significativas (ADR)

Cuando una decisión tecnológica sea suficientemente significativa, puede
requerir un ADR con este modelo (sin crear ADRs en F0-S6 salvo que un
entregable lo exija; ninguno lo exige):

```text
Context
→ Problem
→ Options
→ Criteria
→ Decision
→ Consequences
```

## 5. Gobernanza de incorporación

Una herramienta puede incorporarse únicamente cuando: existe una
necesidad; se evalúan alternativas; se conocen riesgos; se determina su
responsabilidad; se conocen sus permisos; se considera mantenibilidad,
coste, lock-in y reemplazabilidad; y existe validación posterior a la
adopción. Sin estos diez puntos, la incorporación queda
PENDIENTE DE DECISIÓN.

## 6. Reproducibilidad (capacidad evolutiva)

```text
Machine
+
Repository
+
Dependencies
+
Configuration
+
Scripts
+
Documentation
=
Reproducible Environment
```

Las configuraciones importantes se documentan; se minimiza lo manual no
registrado; el entorno debe poder reconstruirse progresivamente. En F0-S6
la reproducibilidad es dirección, no mecanismo implementado.
