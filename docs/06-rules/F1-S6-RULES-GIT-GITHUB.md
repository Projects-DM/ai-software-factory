# F1-S6-RULES-GIT-GITHUB — Rules de Git y GitHub

Fase: F1 — Rules. Sprint: F1-S6. Categoría: RC-05 (Git / GitHub).
Serie `R-GH-NNN` (formato `R-<CAT>-<NNN>` F1-S1). Todas: PROPOSED
v0.1 — definidas ≠ aprobadas ≠ activas. Normativo y portable: Git =
control de versiones local; GitHub = plataforma colaborativa/remota;
ninguno es autoridad normativa; sin enforcement, automatización,
Actions, permisos técnicos ni credenciales.

## Convenciones comunes

Categoría RC-05. Precedencia: especializan R-GB-003/005/008/009/010,
R-CK-003/009/010, R-MS-001/003/007/008 y R-TQ-001/006/007/008 para
Git/GitHub sin duplicarlos; ceden ante RC-08/RC-10/RC-11.
Dependencias: las anteriores + P03/P05/P06/P09/P10/P13/P14/P15/P16/
P17/P18/P19/P26, F0-S5, F0-S7 C01–C06. Autoridad de aprobación:
humana designada C04; excepciones formales (C04+, C05+ temporal
MUST NOT). Revisión: triggers F0-S7 §21. Historial: inicial.

## Distinciones (§7)

`GIT ≠ GITHUB`, `BRANCH ≠ TASK`, `COMMIT ≠ VALIDATION`, `COMMIT ≠
REVIEW`, `PUSH ≠ MERGE`, `PR ≠ APPROVAL`, `APPROVAL ≠ MERGE`, `MERGE
≠ DEPLOYMENT`, `EXECUTION ≠ SUCCESS`, `EVIDENCE ≠ VALIDATION`,
`CAPABILITY ≠ AUTHORIZATION`. Modelo: OBJECTIVE→TASK→BRANCH→COMMIT→
PUSH→PR→REVIEW→APPROVAL→MERGE→VERIFICATION→RESULT; ninguna etapa se
presume por la anterior.

## R-GH-001 — Cambio Git vinculado a Task

Propósito: todo cambio reconstruible hasta su tarea (P13). Alcance:
cambios Git. Obligatoriedad MUST. Severidad HIGH. Condición: al crear
o detectar un cambio. Acción: vincularlo a Task identificable
(TASK→CHANGE→BRANCH→COMMIT→PR→MERGE→VERIFICATION); lo fuera de
alcance activa R-MS-001/003. Restricción: prohibido cambio local
huérfano en trabajo relevante; ningún cambio local es tarea válida
por sí mismo. Excepción: formal C04+ (C01 triviales). Evidencia:
vínculo Task↔cambio. Versión v0.1. Estado PROPOSED.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-GB-003, R-CK-003, R-MS-001, P13 · Relación: especializa R-GB-010/R-MS-008; complementa R-MS-001 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).

## R-GH-002 — Rama separada por unidad de trabajo

Propósito: separación del trabajo y base conocida (P05, P10).
Alcance: branches. Obligatoriedad MUST. Severidad MEDIUM. Condición:
al iniciar trabajo no trivial. Acción: operar en rama separada
trazada a su Task y base; mantener estado esperado conocido.
Restricción: prohibido mezclar unidades de trabajo en una rama sin
justificación. Excepción: formal C04+. Evidencia: rama↔Task↔base.
Versión v0.1. Estado PROPOSED.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-GB-003, R-MS-001, P05/P10 · Relación: complementa R-MS-001 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).

## R-GH-003 — Condiciones del commit

Propósito: commit = unidad de cambio identificable, no veredicto
(P13, P18). Alcance: commits. Obligatoriedad MUST. Severidad HIGH.
Condición: antes de confirmar. Acción: verificar alcance autorizado,
mensaje que identifica Task/motivo, y preservación de historial.
Restricción: `COMMIT ≠ VALIDATION/REVIEW/APPROVAL`; prohibido
presentarlo como prueba de funcionamiento. Sin cantidad impuesta.
Excepción: formal C04+. Evidencia: commit trazable. Versión v0.1.
Estado PROPOSED.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-GB-010, R-MS-008, P13/P18/P19 · Relación: especializa R-GB-010 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).

## R-GH-004 — Condiciones del push

Propósito: `LOCAL COMMIT ≠ PUSH ≠ REMOTE INTEGRATION` (P13).
Alcance: pushes. Obligatoriedad MUST. Severidad HIGH. Condición:
antes de publicar. Acción: verificar rama, destino y trazabilidad
preservada. Restricción: prohibido interpretar push como autorización
de merge. Excepción: formal C04+. Evidencia: registro push↔rama.
Versión v0.1. Estado PROPOSED.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-MS-008, P13 · Relación: complementa R-MS-008 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).

## R-GH-005 — PR preparado

Propósito: PR = propuesta formal, nada más (P03). Alcance: Pull
Requests. Obligatoriedad MUST. Severidad HIGH. Condición: al proponer
integración. Acción: crear PR solo con alcance verificado, evidencia
vinculada y base conocida. Restricción: `creado ≠ revisado ≠ aprobado
≠ integrado`; prohibido presentarlo como validación o certificación.
Excepción: formal C04+. Evidencia: PR + evidencias vinculadas.
Versión v0.1. Estado PROPOSED.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-GB-006, R-TQ-001, P03 · Relación: base para RC-10 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).

## R-GH-006 — Review / Approval / Merge / Verification

Propósito: cuatro actos distintos, cuatro responsables posibles (P10).
Alcance: integración. Obligatoriedad MUST. Severidad HIGH. Condición:
en cada transición. Acción: REVIEW evalúa; APPROVAL autoriza según
nivel; MERGE integra; VERIFICATION comprueba lo integrado.
Restricción: prohibido sustituir una etapa por otra; `APPROVAL ≠
MERGE ≠ CERTIFICATION`. Excepción: ninguna para la separación.
Evidencia: cada acto registrado. Versión v0.1. Estado PROPOSED.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-GB-006, R-TQ-007, P10, F0-S7 · Relación: base para RC-10 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).

## R-GH-007 — Protección conceptual de main y ramas relevantes

Propósito: `main` no es una rama más (P05, P09). Alcance: ramas
compartidas. Obligatoriedad MUST. Severidad CRITICAL. Condición:
siempre. Acción: integrar solo con evidencia, revisión y autorización
correspondientes; preservar integridad. Restricción: prohibidas
modificaciones no autorizadas o sin evidencia. Protección conceptual,
no configuración técnica. Excepción: ninguna (la vía es autorización,
no excepción). Evidencia: autorización + evidencia por integración.
Versión v0.1. Estado PROPOSED.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-GB-004, R-MS-006, P05/P09 · Relación: complementa R-MS-006 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).

## R-GH-008 — Cambios locales inesperados

Propósito: nada es basura presunta (P14, P18). Alcance: cambios no
identificados. Obligatoriedad MUST. Severidad HIGH. Condición: al
detectarlos. Acción: DETECT→PRESERVE→UNDERSTAND→DETERMINE
AUTHORITY→CONTINUE OR ESCALATE. Restricción: prohibidos reset,
checkout destructivo, clean, restore destructivo, sobrescritura o
eliminación automáticos; evidencia antes de lo destructivo.
Excepción: formal C04+. Evidencia: hallazgo + decisión. Versión v0.1.
Estado PROPOSED.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-GB-008/010, R-MS-007, P14/P18 · Relación: especializa R-GB-008 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).

## R-GH-009 — Conflictos

Propósito: resolver con autoridad, sin ampliar alcance (P05, P06).
Alcance: conflictos Git/GitHub. Obligatoriedad MUST. Severidad HIGH.
Condición: al detectarlos. Acción: DETECT→PRESERVE EVIDENCE→
UNDERSTAND→RESOLVE WITH AUTHORITY→VALIDATE→CONTINUE. Restricción:
prohibidos requisitos nuevos, cambios no autorizados, refactors
oportunistas o ampliación de sprint con excusa del conflicto.
Excepción: formal C04+. Evidencia: conflicto + resolución validada.
Versión v0.1. Estado PROPOSED.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-GB-008, R-MS-007, P05/P06 · Relación: especializa R-GB-008/R-MS-007 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).

## R-GH-010 — Operaciones destructivas

Propósito: lo irreversible exige parada y espera (P14, P17).
Alcance: operaciones que eliminan, sobrescriben, alteran historial,
pierden evidencia o afectan ramas compartidas/integración.
Obligatoriedad MUST NOT (ejecutarlas sin el protocolo). Severidad
CRITICAL. Condición: siempre. Restricción: prohibida ejecución sin
STOP→PRESERVE EVIDENCE→ESCALATE→WAIT y autorización registrada.
Reversibles/controlables: comprobar impacto y conservar resultado vía
historial. Excepción: solo temporal C05+. Evidencia: autorización +
estado previo. Versión v0.1. Estado PROPOSED.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales (C05+ temporal) · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-GB-008, R-MS-006/007, P14/P17 · Relación: especializa R-GB-008 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).

## R-GH-011 — Preservación de historial y trazabilidad

Propósito: reconstruir el recorrido sin reescritura silenciosa (P13,
P19). Alcance: historial y cadena OBJECTIVE→…→RESULT con qué/por
qué/rama/commit/revisión/autorización/integración/verificación.
Obligatoriedad MUST. Severidad HIGH. Condición: siempre. Acción:
preservar historial relevante; traza portable (no atada a una UI de
GitHub). Restricción: prohibidas modificaciones silenciosas del
historial; el estado actual no sustituye al proceso. Excepción:
formal C04+. Evidencia: historial + cadena. Versión v0.1. Estado
PROPOSED. Relación: especializa R-GB-010/R-CK-010/R-MS-008/R-TQ-008.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-GB-010, R-CK-010, R-MS-008, R-TQ-008, P13/P19 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).

## R-GH-012 — Sincronización sin confusión

Propósito: `SYNC ≠ TASK COMPLETION` (P03). Alcance: sincronización
con base. Obligatoriedad MUST. Severidad MEDIUM. Condición: con
branch desactualizada o antes de integrar. Acción: sincronizar sin
ocultar ni sobrescribir cambios sin autorización; validar después.
Restricción: prohibido presentar branch sincronizada como tarea
terminada. Excepción: formal C04+. Evidencia: sincronización +
validación posterior. Versión v0.1. Estado PROPOSED.
Contrato: Categoría RC-05 · Autoridad: aprobación C04, excepciones formales · Precedencia: especializa base RC-01; cede ante RC-08/10/11 · Dependencias: R-MS-001, P03 · Relación: complementa R-MS-001 · Revisión: triggers F0-S7 §21 · Historial: inicial (ver §Convenciones comunes).
