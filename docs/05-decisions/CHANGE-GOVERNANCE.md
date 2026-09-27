# CHANGE-GOVERNANCE — AI Software Factory — F0-S7 Gobernanza de cambios

Fase: F0 — Fundaciones.
Sprint: F0-S7 — Gobernanza y decisiones.
Estado del modelo: CONCEPTUAL. No implementado.

Este documento gobierna cómo cambian la Factory y sus instrumentos:
clasificación por impacto, autorización proporcional, implementación,
validación, documentación y cierre. Todo cambio relevante se relaciona
con la decisión que lo autoriza; todo cambio significativo queda
trazado.

## 1. Clasificación

```text
C01 — Trivial (registro mínimo: p. ej. errata sin impacto)
C02 — Operativo (responsable del ámbito + evidencia)
C03 — Técnico (responsable técnico + revisión)
C04 — Arquitectónico (ADR + aprobación humana)
C05 — Estratégico (autoridad humana designada)
C06 — Fundacional (autoridad humana final + revisión de impacto sistémico)
```

El nivel de gobernanza aumenta con el impacto. Estas categorías no son
una matriz automática de permisos (pertenece a fases posteriores): son
criterio conceptual de proporcionalidad.

## 2. Cambios arquitectónicos

Considerar: problema, arquitectura actual, propuesta, alternativas,
impacto, riesgos, reversibilidad, evidencia, compatibilidad, migración
y validación. Modelo:

```text
Need
↓
Architecture Analysis
↓
Options
↓
ADR
↓
Human Approval
↓
Implementation
↓
Validation
↓
Evidence
```

Modelo conceptual, no procedimiento técnico implementado.

## 3. Cambios de herramientas

Coherente con F0-S6 (Need → Evaluation → Decision → Adoption →
Validation):

```text
Current Tool
↓
Problem / Need
↓
Evaluation
↓
Alternatives
↓
Decision
↓
Migration
↓
Validation
```

Considerar: coste, seguridad, mantenimiento, compatibilidad,
automatización, lock-in, impacto sobre Agents, impacto sobre Skills y
recuperación. No se introduce ninguna herramienta nueva en F0-S7.

## 4. Impacto y autorización

Todo cambio declara su impacto (alcance, riesgo, reversibilidad,
afectados) antes de ejecutarse; la autorización corresponde al nivel de
la sección 1 según ese impacto. Sin autorización del nivel
correspondiente no hay implementación legítima (`Capability ≠
Authority`).

## 5. Implementación, validación y documentación

Implementar solo lo autorizado; validar contra criterios con evidencia
externa al propio cambio (`IMPLEMENTED ≠ VALIDATED`); documentar qué
cambió, por qué, con qué autorización y con qué evidencia. Cierre: el
cambio queda en estado final trazado (válido, revertido o superseded)
vinculado a su decisión.

## 6. Relación con ADR

C04–C06 exigen ADR (propuesta en `ADR-INDEX.md`, formato en
`ADR-TEMPLATE.md`); C02–C03 usan registro trazado mínimo; C01 solo
registro. La decisión precede al cambio; el cambio remite a la
decisión.

## 7. Excepciones

Desviación temporal y autorizada (Reason, Risk, Scope, Authorization,
Duration, Evidence, Review). Nunca se convierte automáticamente en
regla; si se vuelve permanente o recurrente, se revisa el sistema que
la originó mediante cambio gobernado.
