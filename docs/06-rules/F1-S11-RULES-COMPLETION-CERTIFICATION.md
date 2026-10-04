# F1-S11-RULES-COMPLETION-CERTIFICATION — Rules de finalización y certificación

Fase: F1 — Rules. Sprint: F1-S11. Categoría: RC-10 (Completion /
Certification). Serie `R-CC-NNN` (formato `R-<CAT>-<NNN>` F1-S1).
Todas: PROPOSED v0.1 — definidas ≠ aprobadas ≠ activas. Cada Rule
contiene explícitos sus 20 campos F1-S1. Normativo: contrato de
cierre, sin Task Manager, Orchestrator, Agents, Skills, workflows,
CI/CD, dashboards, despliegue ni código.

Principio: `EXECUTION ≠ SUCCESS`, `IMPLEMENTED ≠ VALIDATED`,
`VALIDATED ≠ CERTIFIED`, `CERTIFIED ≠ COMPLETED`;
`CAPABILITY ≠ AUTHORITY`, `AUTONOMY ≠ CERTIFICATION AUTHORITY`.

## Distinciones (§8)

`EXECUTION ≠ IMPLEMENTATION/SUCCESS`, `IMPLEMENTATION ≠
VALIDATION`, `VALIDATION ≠ REVIEW/CERTIFICATION`, `REVIEW ≠
CERTIFICATION`, `CERTIFICATION ≠ DEPLOYMENT`, `DEPLOYMENT ≠
COMPLETION`, `EVIDENCE ≠ VALIDATION`, `APPROVAL ≠ CERTIFICATION`,
`COMMIT/MERGE ≠ COMPLETION`. Lifecycle F0-S5 y excepcionales
vigentes; no todo trabajo atraviesa todos los estados (omisión
justificada por tipo/alcance/impacto/riesgo/criterios/Rules).

## Régimen vinculante de excepciones

Todas las menciones `formal C04+` de estas Rules denotan autoridad
mínima dentro del régimen formal (CONDITION→SCOPE→IMPACT→
AUTHORITY→AUTHORIZATION→DURATION→EVIDENCE→REVIEW→REVOCATION/
EXPIRATION) y el régimen C01–C06; nunca autorización genérica.
Ninguna excepción: declara éxito sin evidencia, convierte ausencia
en éxito, elimina validación obligatoria, certifica sin fórmula,
relaja integridad/seguridad, legitima retrospectivamente ni modifica
C01–C06.

## R-CC-001 — Ejecutar, implementar y éxito

ID R-CC-001. Nombre: Ejecutar, implementar y éxito. Propósito:
ejecución = ocurrió; implementación = cambios previstos en alcance
con artefactos y evidencia; éxito = EXPECTED OUTCOME + EVIDENCIA
SUFICIENTE + VALIDACIÓN REQUERIDA + REVIEW APLICABLE + SIN BLOQUEO
(nunca afirmación del ejecutor). REVIEW APLICABLE: necesidad y
profundidad según tipo de trabajo, alcance, impacto, riesgo,
criterios, Rules aplicables y proporcionalidad (coherente R-CC-010);
obligatoria cuando una Rule la exige (`VALIDATION ≠ REVIEW`).
Alcance: toda unidad. Categoría RC-10. Obligatoriedad MUST.
Severidad HIGH. Condición: al cerrar ejecución/implementación.
Acción: verificar artefactos, alcance y evidencia antes de declarar.
Restricción: prohibido declarar éxito por fin de ejecución, commit,
PR, merge, despliegue o dicho del agente. Excepción: formal
C04+. Autoridad: autoridad competente C01–C06. Precedencia:
especializa R-GB-006. Dependencias: R-GB-006, R-MS-001, P03.
Relación: base de R-CC-002…005. Evidencia: artefactos + verificación.
Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21.
Historial: inicial.

## R-CC-002 — Puerta de validación

ID R-CC-002. Nombre: Puerta de validación. Propósito: EXPECTED →
EXECUTE/TEST → OBSERVED → COMPARE → EVIDENCE → VALIDATION con
criterios, esperado/observado, pruebas, regresiones y
proporcionalidad. Alcance: pre-avance. Categoría RC-10.
Obligatoriedad MUST. Severidad HIGH. Condición: antes de avanzar de
estado. Acción: exigir validación contra criterios con evidencia.
Restricción: prohibido avanzar sin ella. Excepción: formal C04+.
Autoridad: autoridad competente. Precedencia: especializa R-TQ-001/
002. Dependencias: R-TQ-001/002/004, P03. Relación: opera R-TQ sin
redefinirlo. Evidencia: veredicto + comparación. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-CC-003 — Revisión previa a certificación

ID R-CC-003. Nombre: Revisión previa a certificación. Propósito:
revisar Rules, alcance, calidad, evidencia, traza, riesgos,
pendientes y preparación (`VALIDATION ≠ REVIEW`; no es lectura).
Alcance: pre-certificación. Categoría RC-10. Obligatoriedad MUST.
Severidad HIGH. Condición: tras validación. Acción: revisar y
dejar constancia. Restricción: prohibido certificar sin revisión.
Excepción: formal C04+. Autoridad: revisor competente
(`EXECUTOR ≠ REVIEWER ≠ CERTIFIER` cuando aplique). Precedencia:
opera con RC-04/08. Dependencias: R-TQ-007, P10. Relación:
puerta de R-CC-004. Evidencia: constancia de revisión. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-CC-004 — Certificación formal

ID R-CC-004. Nombre: Certificación formal. Propósito:
IMPLEMENTED + VALIDATED + REVIEWED + EVIDENCIA SUFICIENTE + SIN
CRÍTICAS PENDIENTES + CERTIFICACIÓN AUTORIZADA = CERTIFIED.
Alcance: aceptación formal. Categoría RC-10. Obligatoriedad MUST.
Severidad CRITICAL. Condición: cumplidos los 6 sumandos. Acción:
certificar solo la autoridad competente C01–C06 (integrada con
F1-S7/F1-S9); `EXECUTION/AUTONOMY/CAPABILITY ≠ CERTIFICATION
AUTHORITY`. Restricción: prohibidas autocertificación, certificación
sin validación y certificación por autonomía. Excepción: ninguna
para la fórmula. Autoridad: certificador competente conforme al
régimen existente C01–C06 (F1-S7/F1-S9, no redefinido), según
alcance, impacto, sensibilidad, condiciones, precedencia, riesgo y
autoridad competente; C04+ no es nivel nuevo ni autorización
universal. Precedencia: base RC-10. Dependencias: R-TQ-007, R-SP-003,
R-AH-005, P02. Relación: consume R-CC-001…003. Evidencia: acto de
certificación. Versión v0.1. Estado PROPOSED. Revisión: triggers
F0-S7 §21. Historial: inicial.

## R-CC-005 — Completion y Definition of Done

ID R-CC-005. Nombre: Completion y Definition of Done. Propósito:
COMPLETED = cierre según objetivo/lifecycle con evidencia de
condiciones; DoD proporcional (objetivo, alcance, entregables,
aceptación, validación, evidencia, revisión, autoridad, cierre,
excepciones). Alcance: cierre. Categoría RC-10. Obligatoriedad MUST.
Severidad HIGH. Condición: al cerrar. Acción: verificar DoD; donde
las Rules exijan certificación, sin ella no hay COMPLETED
(`CERTIFIED ≠ COMPLETED`; `MERGED/DEPLOYED ≠ COMPLETED`).
Restricción: prohibido cerrar por código/PR/aprobación/merge/
despliegue solos; prohibido DoD burocrático idéntico.
Excepción: formal C04+. Autoridad: autoridad competente.
Precedencia: opera con RC-04/05/10. Dependencias: R-CC-004, R-MS-001,
P03. Relación: consume R-CC-004. Evidencia: DoD cumplido. Versión
v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial:
inicial.

## R-CC-006 — Transiciones de estado evidenciadas

ID R-CC-006. Nombre: Transiciones de estado evidenciadas. Propósito:
CURRENT STATE → CONDITION → EVIDENCE → VALIDATION → AUTHORIZED
DECISION → NEW STATE; nunca por tiempo, herramienta, afirmación,
presión o commit. Alcance: lifecycle F0-S5. Categoría RC-10.
Obligatoriedad MUST. Severidad HIGH. Condición: en cada transición.
Acción: exigir condición+evidencia+decisión autorizada, con
formalidad, profundidad y naturaleza proporcionales a tipo,
alcance, impacto, riesgo, reversibilidad, incertidumbre y Rules
aplicables (sin ceremonia de certificación para bajo impacto).
Restricción: prohibidas transiciones sin fundamento. Excepción:
formal C04+. Autoridad: quien autoriza la transición. Precedencia:
opera con F0-S5. Dependencias: R-GB-011, P03. Relación:
generaliza transiciones. Evidencia: fundamento registrado. Versión
v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial:
inicial.

## R-CC-007 — Condiciones insuficientes y evidencia ausente

ID R-CC-007. Nombre: Condiciones insuficientes y evidencia ausente.
Propósito: sin condición demostrada → permanecer o pasar a
BLOCKED/WAITING_HUMAN/CHANGES_REQUESTED/FAILED según causa;
`NO EVIDENCE ≠ FAILURE PROVEN` pero `NO EVIDENCE ≠ SUCCESS`;
sin evidencia necesaria: mantener/bloquear/escalar/intervenir.
Alcance: carencias. Categoría RC-10. Obligatoriedad MUST. Severidad
HIGH. Condición: al faltar condición/evidencia. Acción: clasificar
y derivar; no inventar evidencia ni convertir ausencia en éxito.
Restricción: prohibido avanzar. Excepción: formal C04+. Autoridad:
autoridad competente. Precedencia: opera con R-CK-008/R-ER-001.
Dependencias: R-CK-008, R-ER-001/002, P06. Relación: complementa
ambas. Evidencia: carencia + derivación. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-CC-008 — Validación fallida y revalidación

ID R-CC-008. Nombre: Validación fallida y revalidación. Propósito:
`VALIDATION FAILED → PRESERVE → CLASSIFY → CORRECT/RECOVER/
ESCALATE → REVALIDATE`; lo modificado tras fallo se revalida si
afecta lo validado. Alcance: fallos de validación. Categoría RC-10.
Obligatoriedad MUST. Severidad HIGH. Condición: al fallar. Acción:
aplicar la secuencia e integrar F1-S5/F1-S8. Restricción: prohibido
dar por válida la corrección sin revalidar. Excepción: formal C04+.
Autoridad: autoridad competente. Precedencia: especializa R-TQ-003/
R-ER-008. Dependencias: R-TQ-003, R-ER-005/008, P14. Relación:
consume ambas. Evidencia: fallo + revalidación. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-CC-009 — Changes requested y reapertura

ID R-CC-009. Nombre: Changes requested y reapertura. Propósito:
REVIEW→CHANGES_REQUESTED→IMPLEMENTING→TESTING→REVIEW con motivo,
alcance, evidencia, condición y esperado preservados; reapertura
trazable ante nueva evidencia/defecto/regresión/cambio autorizado/
condición desconocida/pérdida de validez (sin reescribir historia).
Alcance: devoluciones y reaperturas. Categoría RC-10.
Obligatoriedad MUST. Severidad MEDIUM. Condición: al devolver o
reabrir. Acción: aplicar el ciclo y registrar. Restricción:
prohibido perder historial o reabrir en silencio. Excepción: formal
C04+. Autoridad: quien revisa/reabre con competencia. Precedencia:
opera con F0-S5. Dependencias: R-TQ-007, P19. Relación: opera
CHANGES_REQUESTED. Evidencia: ciclo registrado. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-CC-010 — Proporcionalidad del cierre

ID R-CC-010. Nombre: Proporcionalidad del cierre. Propósito: LOW →
validación simple; BOUNDED/KNOWN → validación + revisión
apropiada; HIGH → validación fuerte + gate humano; CRITICAL/UNKNOWN
→ decisión humana (sin crear niveles de autorización). Alcance:
dimensionamiento. Categoría RC-10. Obligatoriedad MUST. Severidad
MEDIUM. Condición: al planificar cierre. Acción: dimensionar
evidencia/revisión/autoridad al impacto/riesgo/sensibilidad/
reversibilidad/incertidumbre. Restricción: prohibido exigir o
relajar de más. Excepción: formal C04+. Autoridad: autoridad
competente. Precedencia: opera con R-TQ-004. Dependencias: R-TQ-004,
P25. Relación: complementa R-TQ-004. Evidencia: dimensionamiento.
Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21.
Historial: inicial.

## R-CC-011 — Evidencia Git sin sustituciones

ID R-CC-011. Nombre: Evidencia Git sin sustituciones. Propósito:
`COMMIT ≠ VALIDATION`, `PUSH ≠ REVIEW`, `PR ≠ APPROVAL`, `APPROVAL
≠ CERTIFICATION`, `MERGE ≠ COMPLETION`; Git integra evidencia, no
sustituye validación/revisión/certificación/completion. Alcance:
integración. Categoría RC-10. Obligatoriedad MUST. Severidad HIGH.
Condición: al integrar. Acción: usar Git como evidencia vinculada.
Restricción: prohibido cerrar por eventos Git solos. Excepción:
formal C04+. Autoridad: autoridad competente. Precedencia:
especializa R-GH-006/011. Dependencias: R-GH-006/011, P13. Relación:
complementa R-GH. Evidencia: eventos vinculados. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-CC-012 — Estados finales, fallo vs cancelación y aprendizaje

ID R-CC-012. Nombre: Estados finales, fallo vs cancelación y
aprendizaje. Propósito: COMPLETED (condiciones cumplidas),
CERTIFIED (aceptación formal), FAILED (objetivo incumplido con
causa/evidencia/acciones/estado/impacto/decisión, jamás reconvertido
en SUCCESS), CANCELLED (detención deliberada), SUPERSEDED
(sustitución), CLOSED (ciclo cerrado, no necesariamente éxito);
aprendizaje COMPLETION→RESULT→MEASUREMENT→LEARNING→KNOWLEDGE sin
reescribir historia ni auto-cambiar Rules/gobernanza (P18/P19/P25/
P30). Alcance: cierre y post-cierre. Categoría RC-10.
Obligatoriedad MUST. Severidad HIGH. Condición: al cerrar/aprender.
Acción: clasificar estado y registrar aprendizaje. Restricción:
prohibidos sinónimos de estado y reescritura histórica. Excepción:
formal C04+. Autoridad: autoridad competente. Precedencia: opera con
RC-04/11. Dependencias: R-ER-008, R-AH-011, P18/P19/P25/P30.
Relación: consume R-ER-008/R-AH-011. Evidencia: estado +
aprendizaje. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7
§21. Historial: inicial.
