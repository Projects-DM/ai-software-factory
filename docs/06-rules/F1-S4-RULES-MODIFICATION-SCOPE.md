# F1-S4-RULES-MODIFICATION-SCOPE — Rules de modificación y alcance

Fase: F1 — Rules. Sprint: F1-S4. Categoría: RC-03 (Scope /
Modification). Serie de IDs `R-MS-NNN` (MS = serie RC-03, formato
`R-<CAT>-<NNN>` del contrato F1-S1). Todas: PROPOSED v0.1 — definidas
≠ aprobadas ≠ activas ≠ técnicamente aplicadas. Sin enforcement ni
mecanismos técnicos.

Principio rector: una modificación autorizada permanece dentro del
alcance autorizado; ampliarlo exige decisión explícita y trazable,
nunca autorización implícita.

## Convenciones comunes (contrato F1-S1)

Categoría RC-03 (todas). Precedencia: especializan la base RC-01
(R-GB-003/005) y operan junto a RC-02 (R-CK-003/009/010) sin
duplicarlas; ceden ante RC-05…RC-11 específicas según
`RULE-GOVERNANCE.md` §2. Dependencias: R-GB-003/005/008/009/010,
R-CK-003/009/010, P05/P09/P13/P17, F0-S5 (estados), F0-S7 (C01–C06).
Autoridad de aprobación: humana designada C04; excepciones por
mecanismo formal (C04+, C05+ temporal para MUST NOT). Revisión:
triggers F0-S7 §21. Historial: inicial. Evidencia por Rule en
WHAT/WHEN/WHO/WHY/RESULT/SOURCE.

## Qué es una modificación

Toda alteración observable de código, documentación, configuración,
estructura de archivos, dependencias, tests, scripts,
automatizaciones o archivos generados dentro del repositorio. Evaluar
una modificación no es ejecutarla.

## R-MS-001 — Alcance autorizado de modificación

Propósito: solo lo perteneciente al objetivo autorizado se modifica
(P05, P09). Alcance: toda modificación en Task. Obligatoriedad MUST.
Severidad HIGH. Condición: antes de modificar. Acción: comprobar
`Task autorizada → Alcance autorizado → Modificación permitida`;
ante modificación descubierta fuera de alcance: STOP / ESCALATE.
Restricción: prohibido modificar fuera del alcance autorizado.
Excepción: mecanismo formal (C04+ con redefinición de Task).
Evidencia: verificación de pertenencia. Versión v0.1. Estado
PROPOSED. Relación: especializa R-GB-003.

## R-MS-002 — Modificación solicitada vs no solicitada

Propósito: clasificar antes de tocar (solicitada, implícitamente
necesaria, conveniente-no-necesaria, no relacionada, oportunista,
refactor no solicitado, colateral). Alcance: toda modificación
propuesta. Obligatoriedad MUST. Severidad HIGH. Condición: al
identificar un cambio. Acción: clasificarlo; solo solicitadas e
implícitamente necesarias con justificación proceden; lo conveniente
u oportunista requiere autorización separada. Restricción: prohibido
convertir oportunidad de mejora en autorización implícita.
Excepción: mecanismo formal (C04+). Evidencia: clasificación +
justificación. Versión v0.1. Estado PROPOSED.

## R-MS-003 — Ampliación del alcance

Propósito: distinguir completar dentro del alcance de cambiar el
alcance para completar (P05, P09). Alcance: Tasks cuyo objetivo
exige tocar lo no incluido. Obligatoriedad MUST. Severidad HIGH.
Condición: al detectar necesidad fuera del alcance original. Acción:
detener la ampliación; someterla a autorización (redefinición de
Task o decisión C04+); solo continuar tras aprobación registrada.
Restricción: prohibida la ampliación silenciosa. Excepción:
mecanismo formal (C04+). Evidencia: solicitud + autorización.
Versión v0.1. Estado PROPOSED. Relación: especializa R-GB-003.

## R-MS-004 — Preservación del trabajo existente

Propósito: no arreglar una cosa rompiendo otra (P05). Alcance:
sobrescrituras, eliminaciones, cambios destructivos, funcionalidad
existente, colaterales, regresiones. Obligatoriedad MUST. Severidad
HIGH. Condición: antes de modificar lo existente. Acción: evaluar
impacto; preferir reversibilidad (P17); preservar funcionalidad
válida salvo objetivo explícito en contra. Restricción: prohibidos
sobrescritura innecesaria, eliminación injustificada y destrucción
sin autorización. Excepción: mecanismo formal (C04+). Evidencia:
evaluación de impacto. Versión v0.1. Estado PROPOSED. Relación:
especializa R-GB-005 al ámbito modificación.

## R-MS-005 — Naturaleza diferenciada de modificación

Propósito: no todas las naturalezas pesan igual (código,
documentación, configuración, estructura, dependencias, tests,
scripts, automatizaciones, generados). Alcance: tipificación previa.
Obligatoriedad MUST. Severidad MEDIUM. Condición: al clasificar una
modificación. Acción: asignar naturaleza e impacto correspondiente;
aplicar el nivel de autorización y evidencia proporcional (mayor
impacto → mayor exigencia, sin matriz de riesgos nueva).
Restricción: prohibido tratarlas todas con el mismo umbral.
Excepción: mecanismo formal (C04+). Evidencia: naturaleza + impacto
asignados. Versión v0.1. Estado PROPOSED.

## R-MS-006 — Cambios de alto impacto

Propósito: detener lo que toca arquitectura, seguridad, datos,
permisos, producción, comportamiento crítico, integridad del sistema
u otras áreas. Alcance: modificaciones listadas. Obligatoriedad
MUST. Severidad CRITICAL. Condición: al detectar alto impacto.
Acción: STOP + PRESERVE EVIDENCE + ESCALATE + WAIT FOR
AUTHORIZATION; continuar solo tras autorización registrada.
Restricción: prohibido continuar por criterio propio. Excepción:
ninguna para la detención; la continuación exige autorización
C04+/C05+ según caso. Evidencia: causa + autorización. Versión v0.1.
Estado PROPOSED. Relación: base para RC-06/RC-07/RC-08 (no las
anticipa).

## R-MS-007 — STOP / PRESERVE / ESCALATE / WAIT / CONTINUE

Propósito: secuencia obligatoria ante ampliación o impacto (P14).
Alcance: condiciones R-MS-001/003/006. Obligatoriedad MUST.
Severidad CRITICAL. Condición: ampliación detectada o alto impacto.
Acción: STOP → PRESERVE EVIDENCE → ESCALATE → WAIT FOR
AUTHORIZATION → CONTINUE solo autorizado. Restricción: prohibido
resolver silenciosamente ampliaciones; prohibido CONTINUE sin
autorización. Excepción: ninguna. Evidencia: cada paso trazado.
Versión v0.1. Estado PROPOSED. Relación: especializa R-GB-008/009.

## R-MS-008 — Trazabilidad de modificación

Propósito: cadena TASK → AUTHORIZED SCOPE → MODIFICATION → REASON →
AUTHORIZATION → EVIDENCE → VALIDATION como obligación conceptual.
Alcance: toda modificación relevante. Obligatoriedad MUST. Severidad
HIGH. Condición: al ejecutar y cerrar cada modificación. Acción:
vincular eslabones; documentar razón; preservar evidencia.
Restricción: prohibidas modificaciones huérfanas en cambios
relevantes. Excepción: mecanismo formal C04+ (C01 triviales).
Evidencia: la cadena (meta). Versión v0.1. Estado PROPOSED.
Relación: especializa R-GB-010/R-CK-010 al cambio; implementación
técnica fuera de alcance.
