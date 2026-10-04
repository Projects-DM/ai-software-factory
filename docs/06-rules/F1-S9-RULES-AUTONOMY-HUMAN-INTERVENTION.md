# F1-S9-RULES-AUTONOMY-HUMAN-INTERVENTION — Rules de autonomía e intervención humana

Fase: F1 — Rules. Sprint: F1-S9. Categoría: RC-08 (Autonomy / Human).
Serie `R-AH-NNN` (formato `R-<CAT>-<NNN>` F1-S1). Todas: PROPOSED
v0.1 — definidas ≠ aprobadas ≠ activas. Cada Rule contiene explícitos
sus 20 campos F1-S1. Normativo: autonomía concedida, condicionada,
limitada, revocable y respaldada por evidencia. Sin ejecución
autónoma real, aprobación automática, interfaces, notificaciones ni
infraestructura.

Finalidad: límites verificables para autonomía segura (P01), con
control humano de lo crítico (P02). Rige `CAPABILITY DOES NOT GRANT
AUTHORIZATION`.

## Distinciones (§7)

`CAPABILITY ≠ AUTHORITY ≠ AUTHORIZATION ≠ AUTONOMY ≠ RESPONSIBILITY`;
`AUTONOMY ≠ VALIDATION ≠ CERTIFICATION`; `EXECUTION ≠ SUCCESS ≠
VALIDATION`; `APPROVAL ≠ VALIDATION`; `SUPERVISION ≠ AUTHORIZATION`;
`ESCALATION ≠ FAILURE`; `HUMAN INTERVENTION ≠ HUMAN EXECUTION OF
EVERYTHING`. Capacidad → autorización → autonomía jamás es
automático.

## Modelo (§8)

`RESPONSIBILITY + SCOPE + AUTHORITY + AUTHORIZATION(active) +
LIMITS + CONTEXT + TOOLS + VALIDATION + RECOVERY = AUTHORIZED
AUTONOMY`. Forma compacta del conjunto normativo único de 14
condiciones definido en R-AH-003 (LIMITS = condición 3, verificada
además como restricción transversal en Alcance+Autoridad+
Condiciones). Condición caída → reducir/suspender/detener/escalar
según caso. Niveles A Asistencia / B Supervisada / C Acotada / D
Condicionada por evidencia; `MAYOR AUTONOMÍA → MAYOR EVIDENCIA`,
nunca menor control.

## Régimen vinculante (excepciones y autoridad)

Aplica a todos los campos Excepción y Autoridad de estas Rules.
Excepción formal: CONDITION→SCOPE→IMPACT→AUTHORITY→AUTHORIZATION→
DURATION→EVIDENCE→REVIEW→REVOCATION/EXPIRATION, subordinada a
precedencia mayor. Nunca: autorización ilimitada, vulnerar Rules
superiores, silencio como aprobación, eliminar gates obligatorios o
validación crítica, inseguridad, fuera de alcance, evidencia falsa o
destruida, retry como recovery, autonomía permanente, ni continuación
autónoma en espera de decisión humana obligatoria.
`EXCEPCIÓN FORMAL ≠ DEROGACIÓN ILIMITADA`.
Autoridad: `COMPETENT AUTHORITY + C01–C06 + SCOPE + SENSITIVITY +
CONDITIONS + PRECEDENCE`; C04 no es universal; sin niveles ni roles
nuevos. `AUTHORITY ≠ AUTHORIZATION ≠ APPROVAL ≠ AUTONOMY`.

## R-AH-001 — Autonomía autorizada y sus límites

ID R-AH-001. Nombre: Autonomía autorizada y sus límites. Propósito:
autonomía = concedida+condicionada+limitada+revocable+evidenciada
(Q1–Q5). Alcance: toda actuación autónoma. Categoría RC-08.
Obligatoriedad MUST. Severidad CRITICAL. Condición: antes de actuar
sin gate. Acción: verificar el conjunto normativo único de 14
condiciones (R-AH-003); degradar
ante caída (reducir/suspender/detener/escalar). Restricción:
prohibida autonomía sin base completa; capacidad, simplicidad
aparente, herramienta, éxito previo o velocidad no conceden nada.
Excepción: formal C04+. Autoridad: autoridad competente conforme al régimen C01–C06, considerando alcance, sensibilidad, condiciones y precedencia aplicables. Precedencia: base
RC-08; cede ante RC-10/11. Dependencias: R-GB-004, R-SP-001/003,
P01/P26. Relación: fundamento de R-AH-002…012. Evidencia: base
invocada. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7
§21. Historial: inicial.

## R-AH-002 — Niveles A–D

ID R-AH-002. Nombre: Niveles de autonomía. Propósito: A propone y
humano decide; B ejecuta autorizado bajo supervisión; C decide y
ejecuta en límites (alcance+validación+recuperación+escalado); D
opera independiente solo con evidencia suficiente del conjunto
normativo R-AH-003, proporcional al nivel. Alcance: clasificación de cada delegación. Categoría RC-08. Obligatoriedad MUST. Severidad HIGH. Condición: al conceder.
Acción: asignar nivel mínimo suficiente con sus salvaguardas.
Restricción: prohibido operar en nivel superior al concedido.
Excepción: formal C04+. Autoridad: autoridad competente conforme al régimen C01–C06, considerando alcance, sensibilidad, condiciones y precedencia aplicables. Precedencia: opera
con RC-06. Dependencias: R-SP-001/003, P01/P26. Relación:
complementa R-SP-003. Evidencia: nivel + salvaguardas. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-AH-003 — Condiciones de concesión

ID R-AH-003. Nombre: Condiciones de concesión. Propósito: conjunto
normativo único y numerado de 14 condiciones verificables (1
Objetivo, 2 Alcance, 3 Límites conocidos, 4 Responsabilidad, 5
Autoridad, 6 Autorización válida, 7 Autorización activa, 8 Contexto
suficiente, 9 Herramientas autorizadas, 10 Impacto conocido, 11
Condiciones de éxito, 12 Validación disponible, 13 Recuperación
conocida, 14 Sin conflicto crítico ni incertidumbre crítica;
LIMITS verificado además como restricción transversal).
Alcance: pre-concesión. Categoría RC-08. Obligatoriedad MUST.
Severidad HIGH. Condición: antes de conceder. Acción: comprobar las
14; denegar si falta una. Restricción: prohibido conceder por
sencillez, herramienta, capacidad, historial o velocidad.
Excepción: formal C04+. Autoridad: autoridad competente conforme al régimen C01–C06, considerando alcance, sensibilidad, condiciones y precedencia aplicables. Precedencia: base
RC-08. Dependencias: R-AH-001, R-CK-001/004, P03/P06. Relación:
puerta de R-AH-002. Evidencia: checklist cumplida. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-AH-004 — Intervención humana obligatoria

ID R-AH-004. Nombre: Intervención humana obligatoria. Propósito:
supuestos mínimos definidos (arquitectura, estrategia, alto impacto,
seguridad, permisos, destructivas, fuera de alcance, producción,
incertidumbre crítica, conflicto Rules, autorización ambigua/ausente,
fallo no recuperable, evidencia insuficiente, validación crítica
fallida, excepción alto impacto, integridad). `HUMAN INTERVENTION ≠
HUMAN EXECUTION OF EVERYTHING`: intervenir puede ser revisar,
decidir, aprobar, autorizar, modificar condiciones, limitar, revocar,
detener, solicitar información u ordenar continuación condicionada,
sin ejecutar manualmente el trabajo técnico. Alcance: los supuestos.
Categoría RC-08. Obligatoriedad MUST. Severidad CRITICAL. Condición:
al detectarlos. Acción: derivar a gate/decisión humana; no
convertir técnica en gate (máxima autonomía en límites).
Restricción: prohibido resolver autónomamente. Excepción: ninguna
para la derivación. Autoridad: decide humano competente.
Precedencia: especializa R-GB-008/009. Dependencias: R-GB-008/009,
R-SP-004/007, R-ER-002/007, P02. Relación: consume R-AH-005.
Evidencia: supuesto + derivación. Versión v0.1. Estado PROPOSED.
Revisión: triggers F0-S7 §21. Historial: inicial.

## R-AH-005 — Taxonomía Human Gates

ID R-AH-005. Nombre: Taxonomía Human Gates. Propósito: NO GATE
(autónomo en límites) ≠ REVIEW (revisar antes de continuar/
certificar) ≠ APPROVAL (autorizar antes de ejecutar) ≠ DECISION
(indelegable) ≠ CERTIFICATION (RC-10). Alcance: diseño de puertas.
Categoría RC-08. Obligatoriedad MUST. Severidad HIGH. Condición: al
definir una puerta. Acción: tipificarla y exigir su rito
(`APPROVAL ≠ VALIDATION`; `REVIEW ≠ APPROVAL`). Restricción:
prohibido eludir decisión requerida por autonomía/velocidad/
historial/herramientas/silencio/interpretación favorable.
Excepción: formal C04+. Autoridad: autoridad competente conforme al régimen C01–C06, considerando alcance, sensibilidad, condiciones y precedencia aplicables. Precedencia: opera
con RC-06/10. Dependencias: R-SP-003, F0-S5, P02. Relación:
especializa gates F0-S5. Evidencia: tipo + rito cumplido. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-AH-006 — Transferencia de control

ID R-AH-006. Nombre: Transferencia de control. Propósito: `AUTONOMOUS
EXECUTION → CONDITION → STOP/PRESERVE → ESCALATE → HUMAN
REVIEW/DECISION → AUTHORIZED RESPONSE → VALIDATE → CONTINUE/MODIFY/
STOP`. Alcance: condición que exige humano. Categoría RC-08.
Obligatoriedad MUST. Severidad HIGH. Condición: al detectarla.
Acción: transferir y NO continuar autónomamente mientras se espera
decisión. Restricción: prohibida la continuación en espera.
Excepción: ninguna. Autoridad: decide humano competente.
Precedencia: especializa R-GB-009/R-ER-007. Dependencias: R-GB-009,
R-ER-002/007, F0-S5. Relación: consume R-AH-005. Evidencia:
transferencia + respuesta. Versión v0.1. Estado PROPOSED. Revisión:
triggers F0-S7 §21. Historial: inicial.

## R-AH-007 — Ausencia de respuesta humana

ID R-AH-007. Nombre: Ausencia de respuesta humana. Propósito:
`WAITING FOR HUMAN DECISION ≠ IMPLICIT APPROVAL`: el silencio no
autoriza, no amplía, no aprueba ni permite continuar lo que exige
decisión. Alcance: esperas humanas. Categoría RC-08. Obligatoriedad
MUST. Severidad HIGH. Condición: sin respuesta. Acción: permanecer
en WAITING_HUMAN o BLOCKED según norma aplicable. Restricción:
prohibido continuar por silencio. Excepción: ninguna. Autoridad:
decide humano al responder. Precedencia: opera con F0-S5.
Dependencias: R-GB-009, R-ER-007, P02. Relación: gemela de espera
con R-ER-007. Evidencia: espera + desenlace. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-AH-008 — Devolución a autonomía

ID R-AH-008. Nombre: Devolución a autonomía. Propósito: retorno solo
con condición resuelta, autoridad/autorización/alcance vigentes,
contexto suficiente, riesgo controlado, validación y recuperación
definidas y decisión registrada. Alcance: post-intervención.
Categoría RC-08. Obligatoriedad MUST. Severidad HIGH. Condición:
tras intervención. Acción: reevaluar el conjunto R-AH-003 y
re-conceder explícitamente solo por la autoridad competente según
F1-S7, con traza completa:
INTERVENTION → CONDITION RESOLVED → RE-EVALUATE →
AUTHORITY/AUTHORIZATION CHECK → SCOPE/LIMITS CHECK → AUTONOMY
LEVEL → EXPLICIT RE-GRANT → VALIDATE → CONTINUE.
`HUMAN RESPONSE ≠ AUTOMATIC RE-GRANT OF AUTONOMY`. Restricción: prohibido `INTERVENTION → AUTONOMY`
automático. Excepción: formal C04+. Autoridad: reconcede la autoridad competente conforme al régimen C01–C06 (alcance, sensibilidad, condiciones, precedencia); responder no es reconceder.
Precedencia: opera con R-AH-003. Dependencias: R-AH-003/006, P26.
Relación: cierra R-AH-006. Evidencia: reevaluación + concesión.
Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21.
Historial: inicial.

## R-AH-009 — Revocación, suspensión y expiración

ID R-AH-009. Nombre: Revocación, suspensión y expiración. Propósito:
autonomía no permanente: reducir/suspender/revocar ante cambio de
condiciones, expiración, nueva información, riesgo, validación
fallida, fuera de alcance, cambio de contexto, contradicción,
recuperación desconocida o evidencia insuficiente. Alcance: toda
autonomía concedida. Categoría RC-08. Obligatoriedad MUST. Severidad
HIGH. Condición: cualquiera de las anteriores. Acción: degradar al
nivel seguro (incluida expiración temporal a estado trazable).
Restricción: prohibido mantener autonomía degradada en sus bases.
Excepción: formal C04+ (re-concesión, no prórroga silenciosa).
Autoridad: revoca la autoridad competente conforme al régimen
C01–C06 (alcance, sensibilidad, condiciones, precedencia); "quien
concedió" no es autorización absoluta ni extiende autonomía
silenciosamente. Precedencia: opera con
R-SP-006. Dependencias: R-SP-006, R-AH-001, P26. Relación:
complementa R-SP-006. Evidencia: causa + degradación. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-AH-010 — Evidencia y trazabilidad de autonomía

ID R-AH-010. Nombre: Evidencia y trazabilidad de autonomía.
Propósito: cadena TASK→SCOPE→AUTHORITY→AUTHORIZATION→AUTONOMY
LEVEL→CONDITIONS→ACTION→RESULT→VALIDATION→EVIDENCE (+ intervención:
condición, evidencia, decisión requerida, autoridad, decisión,
autorización, resultado, validación, siguiente estado). Alcance: cada
acto autónomo e intervención. Categoría RC-08. Obligatoriedad MUST.
Severidad HIGH. Condición: al actuar e intervenir. Acción: vincular
eslabones (normativo, sin logging técnico) con trazabilidad
proporcional: triviales → proporcional; relevantes → suficiente;
críticos → completa según impacto y Rules. C01 no exime de trazar.
Restricción: prohibidos
actos/intervenciones huérfanos; ninguna excepción elimina la
trazabilidad normativa. Excepción: formal C04+ (C01), siempre subordinada al régimen general de autoridad y autorización (C01 no exime de trazabilidad; ninguna excepción elimina traza, gates, validación ni permite fuera de alcance, silencio como aprobación, autonomía ilimitada o continuación en espera obligatoria).
Autoridad: autoridad competente conforme al régimen C01–C06, considerando alcance, sensibilidad, condiciones y precedencia aplicables (trazar siempre, incluso C01). Precedencia: especializa la cadena de
traza. Dependencias: R-GB-010, R-CK-010, R-SP-010, P13.
Relación: extiende R-SP-010. Evidencia: la cadena (meta). Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-AH-011 — Validación y aprendizaje de autonomía

ID R-AH-011. Nombre: Validación y aprendizaje de autonomía.
Propósito: `AUTONOMOUS EXECUTION ≠ SUCCESS`; validar proporcional
al impacto (F1-S5/S8); ciclo EXECUTION→RESULT→VALIDATION→EVIDENCE→
MEASUREMENT→LEARNING→REVIEW→DECISION→GOVERNED CHANGE; éxito ≠ autorización
futura; ampliación solo con evidencia+revisión+decisión (P25/P26);
el aprendizaje no modifica Rules, autoridad, autonomía ni gates por
sí mismo. Alcance: post-ejecución autónoma. Categoría RC-08. Obligatoriedad
MUST. Severidad HIGH. Condición: tras ejecutar. Acción: validar y
registrar aprendizaje sin auto-ampliar. Restricción: prohibido
convertir éxito en autonomía permanente. Excepción: formal C04+.
Autoridad: autoridad competente conforme al régimen C01–C06, considerando alcance, sensibilidad, condiciones y precedencia aplicables; la ampliación posterior la decide la gobernanza (esta Rule no amplía nada por sí misma). Precedencia: opera con
RC-04/11. Dependencias: R-TQ-001, R-ER-008, P25/P26. Relación:
puente a RC-11. Evidencia: validación + aprendizaje. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-AH-012 — Least Privilege y responsabilidad en autonomía

ID R-AH-012. Nombre: Least Privilege y responsabilidad en
autonomía. Propósito: `AUTONOMY ≠ RESPONSIBILITY`; autonomía con
alcance/capacidad/autoridad/duración/contexto/nivel mínimos;
responsables de autorizar, conceder, revisar, decidir, validar,
certificar, revocar y continuar (C-niveles y gates F0-S7, sin roles
nuevos). Alcance: diseño de delegación. Categoría RC-08.
Obligatoriedad MUST. Severidad HIGH. Condición: al delegar.
Acción: minimizar y mapear responsabilidades. Restricción:
prohibido usar autonomía como autorización ni desplazar
responsabilidad. Excepción: formal C04+. Autoridad: autoridad competente conforme al régimen C01–C06, considerando alcance, sensibilidad, condiciones y precedencia aplicables. Precedencia: especializa R-SP-002/005/011. Dependencias: R-SP-002/
005/011, P09/P10. Relación: gemela LP con R-SP-002. Evidencia:
mapa mínimo + responsables. Versión v0.1. Estado PROPOSED.
Revisión: triggers F0-S7 §21. Historial: inicial.
