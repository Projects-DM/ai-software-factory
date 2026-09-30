# F1-S5-RULES-TESTING-QUALITY — Rules de testing y calidad

Fase: F1 — Rules. Sprint: F1-S5. Categoría: RC-04 (Testing / Quality).
Serie `R-TQ-NNN` (formato `R-<CAT>-<NNN>` F1-S1). Todas: PROPOSED
v0.1 — definidas ≠ aprobadas ≠ activas. Normativo, sin frameworks,
herramientas, automatización ni enforcement. Factory terms only: sin
OpenCode ni runtime como requisito (adapters futuros, no norma).

## Convenciones comunes

Categoría RC-04. Precedencia: especializan R-GB-006/007 y operan con
R-CK-004/005 y R-MS-004/007/008 sin duplicarlos; ceden ante RC-10
(certificación) y RC-05…RC-11 específicas. Dependencias: R-GB-006/
007/008/009/010, R-CK-004/005, R-MS-004/007/008, P03/P04/P05/P13/
P14/P25/P26/P30, F0-S5, F0-S7 C01–C06. Autoridad de aprobación:
humana designada C04; excepciones formales (C04+, C05+ temporal
MUST NOT). Revisión: triggers F0-S7 §21. Historial: inicial.

## Distinciones (§6 + §8.6)

`EXECUTION ≠ SUCCESS`, `EXECUTION ≠ VALIDATION`, `EVIDENCE ≠
VALIDATION`, `IMPLEMENTED ≠ VALIDATED`, `VALIDATED ≠ CERTIFIED`,
`TEST RESULT ≠ AUTHORIZATION`. Prueba = procedimiento que produce un
resultado observado. Resultado = dato. Evidencia = registro que cumple
§R-TQ-006. Validación = juicio contra criterios. Revisión =
comprobación independiente. Certificación = autorización (RC-10).

## Modelo conceptual (§9)

OBJECTIVE → EXPECTED RESULT → CHANGE → TEST → OBSERVED RESULT →
EVIDENCE → VALIDATION → REVIEW → CERTIFICATION. Cada flecha exige su
Rule; ninguna se presume.

## R-TQ-001 — Ningún éxito sin validación

Propósito: especializa R-GB-006 con mecánica de verificación (P03).
Alcance: toda ejecución y Task. Obligatoriedad MUST. Severidad
CRITICAL. Condición: al pretender declarar éxito o avance. Acción:
exigir validación completada con evidencia suficiente antes de la
declaración. Restricción: prohibido declarar éxito por fin de
ejecución, por resultado no contrastado o por autocertificación.
Excepción: ninguna. Evidencia: veredicto + pruebas vinculadas.
Versión v0.1. Estado PROPOSED.

## R-TQ-002 — Resultado esperado vs observado

Propósito: contraste objetivo, no impresión (P03, P25). Alcance: todo
cambio verificado. Obligatoriedad MUST. Severidad HIGH. Condición:
antes de ejecutar la verificación. Acción: fijar resultado esperado
derivado de criterios; ejecutar; comparar observado vs esperado y
registrar diferencias. Restricción: prohibido definir lo esperado a
posteriori para que coincida. Excepción: formal C04+. Evidencia:
esperado + observado + comparación. Versión v0.1. Estado PROPOSED.

## R-TQ-003 — Taxonomía de fallos y consecuencias

Propósito: cada evento, su respuesta (P14). Alcance: TEST NOT
EXECUTED, TEST FAILED, UNEXPECTED RESULT, INSUFFICIENT EVIDENCE,
VALIDATION FAILED, VALIDATION INCONCLUSIVE, POSSIBLE REGRESSION.
Obligatoriedad MUST. Severidad HIGH. Condición: al producirse
cualquiera. Acción: clasificar y aplicar STOP/PRESERVE/ESCALATE/WAIT/
CONTINUE según gravedad (fallo e inconcluso nunca CONTINUE directo;
jamas FAIL→RETRY→RETRY→RETRY sin diagnóstico, límites y
justificación). Restricción: prohibida la misma consecuencia para
todos. Excepción: formal C04+. Evidencia: clasificación + ruta
aplicada. Versión v0.1. Estado PROPOSED. Relación: especializa
R-GB-007/008 y R-MS-007.

## R-TQ-004 — Proporcionalidad de la validación

Propósito: validación proporcional a naturaleza y alcance del cambio;
sin conteos fijos, matrices, scoring, coberturas técnicas ni
automatización. Alcance: planificación de verificación. Obligatoriedad
MUST. Severidad MEDIUM. Condición: al definir qué verificar. Acción:
dimensionar la verificación al cambio (naturaleza R-MS-005 +
alcance); justificar suficiencia. Restricción: prohibido exigir lo
mismo a todo cambio o validar de menos por prisa. Excepción: formal
C04+. Evidencia: plan proporcional + justificación. Versión v0.1.
Estado PROPOSED.

## R-TQ-005 — Detección conceptual de regresiones

Propósito: preservar comportamiento existente sin test-system (P05).
Alcance: cambios con superficie de impacto. Obligatoriedad MUST.
Severidad HIGH. Condición: antes de aceptar el cambio. Acción:
comparar comportamiento afectado contra baseline conductual previa;
ante posible regresión: STOP + evidencia + escalado (R-MS-004/007).
Restricción: prohibido asumir ausencia de regresión por éxito local.
Excepción: formal C04+. Evidencia: comparación + veredicto. Versión
v0.1. Estado PROPOSED. Relación: complementa R-MS-004.

## R-TQ-006 — Suficiencia de la evidencia

Propósito: `EVIDENCE EXISTS ≠ EVIDENCE IS SUFFICIENT ≠ VALIDATION IS
ESTABLISHED`. Alcance: toda evidencia de validación. Obligatoriedad
MUST. Severidad HIGH. Condición: al presentar evidencia. Acción:
exigir identificabilidad, relación con cambio y esperado, resultado
observado, reproducibilidad cuando corresponda, trazabilidad,
suficiencia y ausencia de invención. Restricción: prohibido avanzar
con evidencia insuficiente. Excepción: formal C04+. Evidencia: lista
de chequeo cumplida (meta). Versión v0.1. Estado PROPOSED.

## R-TQ-007 — Frontera VALIDATED / CERTIFIED

Propósito: validado = criterios cumplidos con evidencia; certificado
= autorización de RC-10 (P03, F0-S7). Alcance: cierre de verificación.
Obligatoriedad MUST. Severidad HIGH. Condición: tras validación
exitosa. Acción: declarar VALIDATED y derivar a certificación sin
presumirla; `TEST RESULT ≠ AUTHORIZATION`. Restricción: prohibido
presentar VALIDATED como CERTIFIED o integrar por veredicto propio.
Excepción: ninguna. Evidencia: veredicto + derivación. Versión v0.1.
Estado PROPOSED. Relación: base para RC-10 (F1-S11).

## R-TQ-008 — Trazabilidad de la validación

Propósito: cadena cambio→prueba→observado→evidencia→validación→
revisión reconstruible (P13). Alcance: cada verificación relevante.
Obligatoriedad MUST. Severidad HIGH. Condición: al verificar y cerrar.
Acción: vincular eslabones al Task ID. Restricción: prohibidos
veredictos huérfanos. Excepción: formal C04+ (C01 triviales).
Evidencia: la cadena (meta). Versión v0.1. Estado PROPOSED. Relación:
especializa R-GB-010/R-CK-010/R-MS-008.
