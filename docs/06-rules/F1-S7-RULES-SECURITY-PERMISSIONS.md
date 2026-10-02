# F1-S7-RULES-SECURITY-PERMISSIONS — Rules de seguridad y permisos

Fase: F1 — Rules. Sprint: F1-S7. Categoría: RC-06 (Security /
Permissions). Serie `R-SP-NNN` (formato `R-<CAT>-<NNN>` F1-S1).
Todas: PROPOSED v0.1. Cada Rule contiene explícitos sus 20 campos
F1-S1 (lección F1-S6: sin sustitución por convenciones). Normativo,
sin autenticación/RBAC/secretos/cifrado/infra ni enforcement técnico.

Finalidad: límites verificables para autonomía segura, no impedir
actuar. Rige `CAPABILITY DOES NOT GRANT AUTHORIZATION`.

## Distinciones (§8)

`CAPABILITY ≠ AUTHORITY ≠ AUTHORIZATION ≠ PERMISSION`; `PERMISSION ≠
EXECUTION`; `ACCESS ≠ NEED`; `ACCESS ≠ AUTHORIZATION`; `VISIBILITY ≠
AUTHORITY`; `AUTHENTICATION ≠ AUTHORIZATION`; `AUTONOMY ≠ AUTHORITY /
RESPONSIBILITY / CERTIFICATION`; `EXECUTION ≠ SUCCESS`; `EVIDENCE ≠
VALIDATION`; `VALIDATION ≠ CERTIFICATION`.

## Modelo de autorización (§9)

`CAPABILITY + SCOPE + AUTHORITY + AUTHORIZATION + CONDITIONS =
PERMITTED ACTION`. Traza: `ACTOR → CAPABILITY → AUTHORITY →
AUTHORIZATION → SCOPE → ACTION → EVIDENCE → VALIDATION → RESULT`.

## R-SP-001 — Capacidad no otorga autorización

ID R-SP-001. Nombre: Capacidad no otorga autorización. Propósito:
ninguna capacidad técnica es permiso (P09, P23). Alcance: todo actor,
agente y proceso. Categoría RC-06. Obligatoriedad MUST. Severidad CRITICAL. Condición: siempre. Acción requerida: verificar
la base de autorización según el caso —AUTHORIZATION válida +
AUTHORIZED SCOPE + CONDITIONS + LEAST PRIVILEGE—: (a)
acción rutinaria con autorización válida, alcance autorizado,
condiciones satisfechas y privilegio mínimo → ejecución autónoma
sin nueva aprobación humana; (b) acción que excede el alcance, es
sensible, de alto impacto, irreversible o difícilmente reversible,
modifica autoridad o permisos, afecta recursos críticos o a
terceros de forma relevante, requiere excepción o así lo exigen las
Rules aplicables → autorización explícita adicional previa; (c)
fuera de alcance → STOP → PRESERVE EVIDENCE → ESCALATE → WAIT;
(d) acción prohibida → no ejecutar. La evidencia se produce y
consolida durante/después (ACTION → EVIDENCE → VALIDATION →
RESULT) y solo es previa cuando una Rule específica la exige; no
toda ejecución rutinaria requiere evidencia preexistente.
Restricción: prohibido actuar
por disponibilidad técnica, urgencia, conveniencia o supuesto
conocimiento previo; prohibido exigir aprobación humana nueva a
rutinas debidamente autorizadas. Excepción:
ninguna (la vía es autorización, no excepción). Autoridad: aprueba
C04; cada acto debe estar respaldado por una base de autorización
válida y trazable, conforme a su alcance, condiciones y nivel de
sensibilidad; las acciones rutinarias dentro de un alcance ya
autorizado no requieren una nueva aprobación humana por cada
ejecución. Precedencia: base RC-06; cede
ante RC-08/10/11. Dependencias: R-GB-004, P09/P23. Relación:
fundamento de R-SP-002…012. Evidencia: base de autorización
invocada + evidencia producida por la acción y su validación
(`AUTHORIZATION ≠ EVIDENCE ≠ VALIDATION`). Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21.
Historial: inicial.

## R-SP-002 — Privilegio mínimo

ID R-SP-002. Nombre: Privilegio mínimo. Propósito: solo lo necesario
para la responsabilidad autorizada (P09). Alcance: acceso a contexto,
recursos, repos, información, herramientas. Categoría RC-06. Obligatoriedad MUST. Severidad HIGH. Condición: al asignar o usar acceso. Acción: limitar a NEED + RELEVANCE + AUTHORIZED SCOPE +
LEAST; preferir temporal sobre permanente. Restricción: prohibidos
acceso innecesario, privilegio excesivo, permanencia injustificada y
uso por disponibilidad (`Disponibilidad técnica ≠ necesidad
legítima`). Excepción: formal C04+. Autoridad: aprueba C04.
Precedencia: especializa R-GB-004; cede ante RC-08/10/11.
Dependencias: R-GB-004, R-CK-001/002, P09/P12/P24. Relación:
complementa R-CK-001. Evidencia: alcance de acceso justificado.
Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21.
Historial: inicial.

## R-SP-003 — Niveles de autorización explícita

ID R-SP-003. Nombre: Niveles de autorización explícita. Propósito:
cada clase de acción, su autorización (P01+P02: autonomía máxima en
límites + control humano crítico). C01–C06 pertenecen al modelo de
gobernanza F0-S7; F1-S7 no crea jerarquía nueva, solo aplica sus
conceptos al ámbito Security & Permissions. Alcance: rutinarias en alcance;
fuera de alcance; sensibles; alto impacto; irreversibles; terceros;
modificadoras de autoridad/permisos; recursos críticos. Categoría RC-06. Obligatoriedad MUST. Severidad HIGH. Condición: antes de
actuar. Acción: clasificar y exigir la autorización correspondiente
(rutina: alcance vigente; resto: explícita de nivel proporcional;
críticas: humana). Restricción: prohibido tratar sensible como
rutinaria; no toda operación exige gate humano. Excepción: formal
C04+. Autoridad: aprueba C04; autorizan niveles C01–C06/gates, cada
uno solo dentro de su ámbito legítimo, sobre acciones bajo su
responsabilidad, con alcance, condiciones y periodo definidos y
respetando precedencia, privilegio mínimo y Rules superiores (ninguna
autoridad posee autorización universal). Precedencia: opera con RC-08 (gates). Dependencias: R-GB-004,
R-MS-006, F0-S5/S7. Relación: base para R-SP-004/005. Evidencia:
clase + autorización. Versión v0.1. Estado PROPOSED. Revisión:
triggers F0-S7 §21. Historial: inicial.

## R-SP-004 — Acciones sensibles

ID R-SP-004. Nombre: Acciones sensibles. Propósito: tratar lo que
afecta seguridad, permisos, datos, información sensible, integridad,
recursos críticos, producción, historial, terceros o límites ajenos.
Alcance: lista §12. Categoría RC-06. Obligatoriedad MUST. Severidad CRITICAL. Condición: ante acción sensible o autorización indeterminable.
Acción: STOP → PRESERVE EVIDENCE → ESCALATE → WAIT FOR
AUTHORIZATION → CONTINUE ONLY IF AUTHORIZED. Restricción: prohibido
justificar por urgencia/conveniencia/disponibilidad/facilidad/
presión/supuesto/implícito. Excepción: ninguna para la detención.
Autoridad: decide humano competente. Precedencia: especializa
R-GB-008. Dependencias: R-GB-008/009, R-MS-006/007. Relación:
complementa R-MS-006. Evidencia: causa + autorización. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-SP-005 — Delegación

ID R-SP-005. Nombre: Delegación. Propósito: delegar sin transferir
autoridad ciega. Alcance: toda delegación. Categoría RC-06. Obligatoriedad MUST. Severidad HIGH. Condición: al delegar. Acción:
hacerla explícita, identificable, limitada en alcance y tiempo cuando
corresponda, trazable, revocable y compatible con la autoridad
origen. Restricción: `DELEGATED CAPABILITY ≠ DELEGATED AUTHORITY`.
Excepción: formal C04+. Autoridad: quien delega dentro de su
autoridad; aprueba C04. Precedencia: cede ante RC-08/11.
Dependencias: R-GB-004, F0-S7. Relación: base para R-SP-006.
Evidencia: delegación registrada. Versión v0.1. Estado PROPOSED.
Revisión: triggers F0-S7 §21. Historial: inicial.

## R-SP-006 — Revocación y expiración

ID R-SP-006. Nombre: Revocación y expiración. Propósito: estados
ACTIVE/REVOKED/EXPIRED/REPLACED/SUSPENDED/REJECTED con efecto
normativo. Alcance: toda autorización. Categoría RC-06. Obligatoriedad MUST. Severidad HIGH. Condición: siempre. Acción:
respetar estado vigente; revocada/suspendida/expirada no fundamenta
continuar; trazar qué autorización regía en cada acción.
Restricción: prohibido operar con autorización no ACTIVE.
Excepción: formal C04+ (re-emisión, no prórroga silenciosa).
Autoridad: revoca quien autorizó o superior; aprueba C04.
Precedencia: cede ante RC-11. Dependencias: R-SP-005, F0-S7.
Relación: complementa R-SP-005. Evidencia: estado + historial.
Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21.
Historial: inicial.

## R-SP-007 — Permisos insuficientes

ID R-SP-007. Nombre: Permisos insuficientes. Propósito: faltante,
insuficiencia, alcance incierto, autorización desconocida,
autoridad indeterminable, conflicto no resuelto, condiciones
insuficientes, incertidumbre relevante, expiración, revocación o
solicitud que excede el alcance conocido → parada segura (el
exceso de privilegio corresponde a R-SP-008, no aquí).
Alcance: los supuestos de insuficiencia, incertidumbre, falta de autorización o exceso del alcance conocido enumerados en esta Rule. Categoría RC-06. Obligatoriedad MUST.
Severidad HIGH. Condición: al detectarlos. Acción: STOP → PRESERVE
EVIDENCE → ESCALATE → WAIT → CONTINUE ONLY WHEN AUTHORIZED.
Restricción: prohibido improvisar, auto-ampliar o usar permisos
superiores disponibles. Excepción: ninguna para la detención.
Autoridad: decide humano competente. Precedencia: especializa
R-GB-008. Dependencias: R-GB-008/009, R-MS-007. Relación:
complementa R-SP-004. Evidencia: causa + ruta. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-SP-008 — Permisos excesivos

ID R-SP-008. Nombre: Permisos excesivos. Propósito: el exceso no
autoriza su uso. Alcance: acceso/capacidad superior a la necesaria.
Categoría RC-06. Obligatoriedad MUST. Severidad MEDIUM. Condición:
al identificarlo. Acción: no usar por conveniencia; mantener mínimo;
preservar traza; escalar si afecta seguridad/control; no convertir
disponibilidad en alcance. Restricción: prohibido normalizar el
exceso. Excepción: formal C04+. Autoridad: aprueba C04. Precedencia:
cede ante RC-08/11. Dependencias: R-SP-002, P09. Relación:
complementa R-SP-002. Evidencia: hallazgo + contención. Versión
v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-SP-009 — Conflictos de autoridad

ID R-SP-009. Nombre: Conflictos de autoridad. Propósito: autorizaciones
contradictorias, autoridades incompatibles, instrucciones fuera de
alcance, delegaciones incompatibles o permisos contra Rule superior.
Alcance: los 5 supuestos. Categoría RC-06. Obligatoriedad MUST.
Severidad HIGH. Condición: al detectarlos. Acción: aplicar
precedencia F1-S1/F0; si irresoluble: STOP → PRESERVE EVIDENCE →
ESCALATE → WAIT. Restricción: prohibida la interpretación
conveniente. Excepción: ninguna. Autoridad: decide humano
competente. Precedencia: según RULE-GOVERNANCE §2. Dependencias:
R-GB-011, F0-S7. Relación: especializa R-GB-011. Evidencia:
conflicto + resolución. Versión v0.1. Estado PROPOSED. Revisión:
triggers F0-S7 §21. Historial: inicial.

## R-SP-010 — Trazabilidad de autorizaciones

ID R-SP-010. Nombre: Trazabilidad de autorizaciones. Propósito:
cadena ACTOR→CAPABILITY→AUTHORITY→AUTHORIZATION→SCOPE→ACTION→
EVIDENCE→VALIDATION→RESULT reconstruible (P13). Alcance: cada acto
autorizado relevante. Categoría RC-06. Obligatoriedad MUST. Severidad HIGH. Condición: al autorizar y ejecutar. Acción: vincular
eslabones. Restricción: prohibidos actos huérfanos de autorización.
Excepción: formal C04+ (C01 triviales). Autoridad: aprueba C04.
Precedencia: cede ante RC-11. Dependencias: R-GB-010, R-CK-010,
R-MS-008, R-TQ-008, R-GH-011, P13. Relación: especializa la cadena
de traza. Evidencia: la cadena (meta). Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-SP-011 — Separación de responsabilidades

ID R-SP-011. Nombre: Separación de responsabilidades. Propósito:
CAPABILITY/AUTHORITY/AUTHORIZATION/EXECUTION/VALIDATION/REVIEW/
CERTIFICATION no se absorben entre sí (P10). Alcance: todo flujo.
Categoría RC-06. Obligatoriedad MUST. Severidad HIGH. Condición:
siempre. Acción: impedir que una capacidad absorba etapas ajenas
(autorizar/validar/revisar/certificar lo propio). Restricción:
prohibida la concentración implícita. Excepción: ninguna.
Autoridad: aprueba C04. Precedencia: base RC-06. Dependencias:
R-GB-004/006, P10. Relación: gemela de R-GB-004 en clave
autorización. Evidencia: mapa acto→etapa→responsable. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-SP-012 — Acceso a contexto y recursos

ID R-SP-012. Nombre: Acceso a contexto y recursos. Propósito:
acceso justificado por NEED + RELEVANCE + AUTHORIZED SCOPE + LEAST
PRIVILEGE (complementa F1-S3). Alcance: información y recursos.
Categoría RC-06. Obligatoriedad MUST. Severidad HIGH. Condición: al
acceder. Acción: justificar necesidad; denegar lo disponible no
necesario (`AVAILABLE ≠ NECESSARY`; `VISIBLE ≠ AUTHORIZED`;
`ACCESSIBLE ≠ AUTHORIZED`). Restricción: prohibido confundir
visibilidad con autorización. Excepción: formal C04+. Autoridad:
aprueba C04. Precedencia: opera con RC-02. Dependencias: R-CK-001/
002/003, R-SP-002, P12/P24. Relación: complementa F1-S3 sin
duplicarlo. Evidencia: justificación de acceso. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.
