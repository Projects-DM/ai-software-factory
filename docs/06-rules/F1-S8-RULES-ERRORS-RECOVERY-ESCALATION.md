# F1-S8-RULES-ERRORS-RECOVERY-ESCALATION — Rules de errores, recuperación y escalamiento

Fase: F1 — Rules. Sprint: F1-S8. Categoría: RC-07 (Errors / Recovery).
Serie `R-ER-NNN` (formato `R-<CAT>-<NNN>` F1-S1; taxonomía RC-07
confirmada). Todas: PROPOSED v0.1 — definidas ≠ aprobadas ≠ activas.
Normativo: qué debe ocurrir, nunca cómo implementarlo. Sin recovery
automática, reintentos automáticos, observabilidad, infraestructura ni
código de recuperación.

## Convenciones comunes

Categoría RC-07. Precedencia: especializan R-GB-007/008/009,
R-MS-007, R-TQ-003 y R-SP-004/007 para error/fallo/recuperación sin
duplicarlos; ceden ante RC-08/10/11. Dependencias: las anteriores +
P01/P02/P03/P05/P06/P09/P13/P14/P15/P16/P17/P18/P19/P20/P25/P26,
F0-S5, F0-S7 C01–C06. Autoridad de aprobación: humana designada C04;
excepciones formales (C04+, C05+ temporal MUST NOT). Revisión:
triggers F0-S7 §21. Historial: inicial.

Límites de la excepción formal (vinculante para todas las fichas):
`EXCEPCIÓN FORMAL ≠ DEROGACIÓN ILIMITADA DE LAS RULES`. Una
excepción no otorga autoridad inexistente, no vulnera Rules
superiores, no autoriza por conveniencia, no permite retry infinito
ni ciego, ocultar fallos, eliminar evidencia, omitir validación
obligatoria, continuar en inseguridad, confundir retry con recovery
ni actuar fuera del alcance autorizado. Estructura siempre:
CONDICIÓN→ALCANCE→IMPACTO→AUTORIDAD→AUTORIZACIÓN→DURACIÓN→
EVIDENCIA→REVISIÓN, subordinada a precedencia mayor.

Régimen de autoridad (vinculante): C04 no es autoridad universal.
Cada acción se respalda en la autoridad competente conforme al
régimen C01–C06 de F0-S7, el alcance, las condiciones, la
sensibilidad y las Rules de mayor precedencia. Se distingue
AUTHORITY (facultad) de APPROVAL (acto documental de la Rule) y de
AUTHORIZATION (permiso del caso): quien aprueba una Rule no autoriza
por ello cada recuperación concreta.

## Distinciones (§5)

`ERROR ≠ FAILURE`, `FAILURE ≠ BLOCKED`, `BLOCKED ≠ RECOVERING`,
`RECOVERING ≠ SUCCESS`, `RETRY ≠ RECOVERY`, `RECOVERY ≠ VALIDATION`,
`VALIDATION ≠ CERTIFICATION`, `EVIDENCE ≠ VALIDATION`, `STOP ≠
CANCEL`, `ESCALATION ≠ FAILURE`.

## Modelo (§8)

EVENT/RESULT → DETECT → CLASSIFY → PRESERVE EVIDENCE → DIAGNOSE →
(RECOVERABLE → RECOVER → VALIDATE → CONTINUE/ESCALATE) / (NOT SAFE o
UNKNOWN → STOP → ESCALATE → WAIT FOR DECISION). Ningún fallo se
presume recuperable.

## R-ER-001 — Clasificación error / fallo / bloqueo / incertidumbre

ID R-ER-001. Nombre: Clasificación error/fallo/bloqueo. Propósito:
cada condición, su régimen (ERROR: sin resultado esperado; FAILURE:
objetivo incumplible en condiciones conocidas; BLOCKED: continuación
ilegítima por faltante; CRITICAL UNCERTAINTY: sin base segura).
Alcance: todo evento adverso. Categoría RC-07. Obligatoriedad MUST.
Severidad HIGH. Condición: al detectarlo. Acción: clasificar antes de
actuar; la clasificación determina el régimen posterior. BLOCKED =
no puede continuarse legítimamente por falta de condición necesaria
(p. ej. DEPENDENCIA NO DISPONIBLE → BLOCKED → NO CONTINUE). STOP =
detención requerida para preservar seguridad, integridad, evidencia
o control (p. ej. RIESGO DE DAÑO → STOP → PRESERVE EVIDENCE →
ESCALATE). Ambos pueden concurrir, pero no son equivalentes.
Restricción: prohibido tratarlas como equivalentes (`FAILURE ≠
BLOCKED`, `STOP ≠ CANCEL`). Excepción: formal C04+. Autoridad: aprueba C04.
Precedencia: especializa R-GB-007/008. Dependencias: R-GB-007/008,
R-CK-008, P06/P14. Relación: base de R-ER-002…009. Evidencia: clasificación. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-ER-002 — Parada segura

ID R-ER-002. Nombre: Parada segura. Propósito: detenerse ante daño
posible, incertidumbre crítica, autorización insuficiente, alcance
excedido, alto impacto no autorizado, evidencia insuficiente/perdida,
recuperación desconocida/insegura, repetición dañina, contradicción
no resuelta o imposibilidad de continuar seguro. Alcance: toda
ejecución. Categoría RC-07. Obligatoriedad MUST. Severidad CRITICAL.
Condición: cualquiera de las anteriores. Acción: STOP preservando
evidencia (`STOP ≠ CANCEL`). Restricción: prohibido continuar.
Excepción: ninguna para la detención. Autoridad: detenerse siempre
autorizado; reanudar exige autoridad del caso. Precedencia:
especializa R-GB-008/R-MS-007. Dependencias: R-GB-008, R-MS-007,
R-SP-004, P14. Relación: gemela de parada con R-SP-004 en clave
recuperación. Evidencia: causa + estado. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-ER-003 — Preservación y diagnóstico

ID R-ER-003. Nombre: Preservación y diagnóstico. Propósito: ninguna
decisión sobre evidencia perdida (P03, P14). Alcance: todo fallo o
bloqueo. Categoría RC-07. Obligatoriedad MUST. Severidad HIGH.
Condición: tras detectar. Acción: PRESERVE EVIDENCE primero
(evidencia disponible, aunque parcial); diagnosticar causa, alcance
e impacto antes de recuperar o reintentar. No tratar evidencia
inexistente como existente; no inventarla; identificar la faltante;
si lo disponible es insuficiente para acción segura, STOP/ESCALATE;
si permite actuar seguro, dejar explícita y trazable la limitación
(P03 sin prohibir toda acción segura; P14).
Restricción: prohibido diagnosticar sin registrar lo disponible o
destruir evidencia al intentar. Excepción: formal C04+. Autoridad: aprueba C04.
Precedencia: opera con RC-04/09. Dependencias: R-GB-010, R-MS-007,
R-TQ-008, P03/P14. Relación: prerrequisito de R-ER-004/005/007.
Evidencia: evidencia + diagnóstico. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-ER-004 — Reintento legítimo vs prohibido

ID R-ER-004. Nombre: Reintento legítimo vs prohibido. Propósito:
`RETRY ≠ RECOVERY`; retry solo si seguro, útil, autorizado,
proporcional y trazable. Alcance: toda repetición. Categoría RC-07.
Obligatoriedad MUST. Severidad HIGH. Condición: antes de repetir.
Acción: verificar las 5 condiciones + causa comprendida; prohibidos
infinito, ciego, destructivo sin evaluación, ocultador, sin causa,
duplicador, destructor de evidencia o agravante. Restricción:
prohibido FAIL→RETRY→RETRY→RETRY sin diagnóstico, límites y
justificación. Excepción: formal C04+. Autoridad: aprueba C04.
Precedencia: especializa R-GB-008. Dependencias: R-GB-008, R-MS-007,
P15. Relación: compuerta previa a R-ER-005. Evidencia: justificación
+ límites + resultado. Versión v0.1. Estado PROPOSED. Revisión:
triggers F0-S7 §21. Historial: inicial.

## R-ER-005 — Recuperación legítima

ID R-ER-005. Nombre: Recuperación legítima. Propósito: volver a
estado conocido y seguro con validación (10 pasos §11: preservar,
comprender, estado conocido, acción autorizada, alcance/autoridad,
no-daño, ejecutar, validar, conservar, siguiente estado). Alcance:
fallos recuperables. Categoría RC-07. Obligatoriedad MUST. Severidad
HIGH. Condición: fallo clasificado recuperable con vía autorizada.
Acción: ejecutar los 10 pasos. RECOVERY es el concepto normativo
de recuperación; ROLLBACK es una posible técnica futura de
restauración al estado previo conocido (corrección controlada,
reanudación desde estado conocido u otra acción autorizada y
validable), nunca su definición ni su implementación.
Restricción: prohibidos oportunismo, fuera de alcance, workaround no
autorizado, retry disfrazado y ocultamiento. Excepción: formal C04+.
Autoridad: aprueba C04; autoriza la vía el nivel competente.
Precedencia: opera con R-MS-001/003 (alcance). Dependencias:
R-MS-001/003/007, R-SP-001, P05/P14/P15. Relación: consume
R-ER-003/004. Evidencia: pasos + validación. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-ER-006 — Idempotencia y reversibilidad

ID R-ER-006. Nombre: Idempotencia y reversibilidad. Propósito:
favorecer operaciones repetibles y reversibles con estado conocido
(P16, P17). Alcance: acciones de recuperación y reintento. Categoría
RC-07. Obligatoriedad MUST. Severidad MEDIUM. Condición: al diseñar
o elegir la acción. Acción: preferir idempotente/reversible/bajo
impacto; ante propiedad UNKNOWN → INCREASE CAUTION y, si
corresponde, STOP→PRESERVE→ESCALATE→WAIT. Restricción: prohibido
asumir idempotencia o reversibilidad. Excepción: formal C04+.
Autoridad: aprueba C04. Precedencia: cede ante RC-08/11.
Dependencias: R-ER-004/005, P16/P17. Relación: condiciona R-ER-004.
Evidencia: propiedades asumidas/declaradas. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-ER-007 — Escalamiento accionable

ID R-ER-007. Nombre: Escalamiento accionable. Propósito: escalar lo
irresoluble con contexto decidible (no un "falló"). Alcance: fuera
de autoridad/conocimiento/alcance. Categoría RC-07. Obligatoriedad
MUST. Severidad HIGH. Condición: cuando la condición no puede
resolverse legítimamente dentro de la autoridad, conocimiento,
alcance y condiciones disponibles; existe condición que requiere
decisión humana; una Rule superior exige escalamiento; o la
continuación segura no puede determinarse. No es obligatorio agotar
una vía cuando ya falta autoridad o alcance. Acción:
escalar CONTEXT→OBJECTIVE→CURRENT STATE→ERROR/FAILURE→EVIDENCE→
ACTIONS→RESULTS→RISK/IMPACT→DECISION REQUIRED; `ESCALATION ≠
FAILURE`. Restricción: prohibido escalar como sustituto de
validación. Excepción: ninguna. Autoridad: decide humano
competente. Precedencia: especializa R-GB-009. Dependencias:
R-GB-009, R-SP-004/007, P02. Relación: gemela de escalado con
R-GB-009. Evidencia: paquete + decisión. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-ER-008 — Continuación validada y cierre

ID R-ER-008. Nombre: Continuación validada y cierre. Propósito:
`RECOVERY → VALIDATION → EVIDENCE → AUTHORIZED CONTINUATION →
SUCCESS/NEXT STATE`; recovery exitosa ≠ tarea/s éxito/
certificación. Alcance: post-recuperación. Categoría RC-07.
Obligatoriedad MUST. Severidad HIGH. Condición: tras recuperar.
Acción: validar, evidenciar y solo continuar autorizado; sin
validación suficiente: NO SUCCESS. Cierre de fallo: causa,
evidencia, acciones, resultados, estado final, impacto y decisión
posterior conservados; FAILURE jamás reconvertido en SUCCESS.
Restricción: prohibido continuar o cerrar sin validación.
Excepción: formal C04+. Autoridad: aprueba C04; autoriza continuar
el nivel competente. Precedencia: opera con RC-04/10. Dependencias:
R-GB-006, R-TQ-001/007, P03. Relación: consume R-ER-005. Evidencia: validación + cierre. Versión v0.1. Estado PROPOSED. Revisión:
triggers F0-S7 §21. Historial: inicial.

## R-ER-009 — Trazabilidad de incidentes

ID R-ER-009. Nombre: Trazabilidad de incidentes. Propósito: cadena
TASK→ACTION→ERROR/FAILURE→EVIDENCE→CLASSIFICATION→DIAGNOSIS→
RECOVERY/STOP→AUTHORIZATION→VALIDATION→RESULT→NEXT STATE con
qué/cuándo/quién/evidencia/acciones/por qué/resultados/autoridad/
validación/estado (P13). Alcance: cada incidente relevante.
Categoría RC-07. Obligatoriedad MUST. Severidad HIGH. Condición:
durante y al cierre. Acción: vincular eslabones (obligación
normativa, sin logging técnico) con trazabilidad proporcional al
impacto: eventos triviales, proporcional; incidentes relevantes,
suficiente; incidentes críticos, completa según impacto y Rules.
Restricción: prohibidos incidentes relevantes huérfanos; ninguna
excepción elimina la trazabilidad normativa (`TRAZABILIDAD
PROPORCIONAL ≠ AUSENCIA`; `EXCEPCIÓN ≠ INCIDENTE HUÉRFANO`). Excepción: formal C04+ (C01 triviales). Autoridad:
aprueba C04. Precedencia: especializa la cadena de traza.
Dependencias: R-GB-010, R-CK-010, R-MS-008, R-TQ-008, R-GH-011,
P13/P18. Relación: especializa R-TQ-008/R-GH-011. Evidencia: la
cadena (meta). Versión v0.1. Estado PROPOSED. Revisión: triggers
F0-S7 §21. Historial: inicial.
