# F1-S10-RULES-DOCUMENTATION-TRACEABILITY — Rules de documentación y trazabilidad

Fase: F1 — Rules. Sprint: F1-S10. Categoría: RC-09 (Documentation /
Traceability). Serie `R-DT-NNN` (formato `R-<CAT>-<NNN>` F1-S1).
Todas: PROPOSED v0.1 — definidas ≠ aprobadas ≠ activas. Cada Rule
contiene explícitos sus 20 campos F1-S1. Normativo y portable: sin
observabilidad, logging, BD, dashboards, agentes ni automatización.
Finalidad: continuidad + comprensión + reconstrucción + trazabilidad
+ conocimiento reutilizable, sin burocracia.

## Distinciones (§7)

`DOCUMENTATION ≠ TRACEABILITY ≠ LOGGING/OBSERVABILITY`;
`DOCUMENTATION ≠ EVIDENCE ≠ VALIDATION`; `REFERENCE ≠ SOURCE ≠
EVIDENCE`; `CURRENT STATE ≠ HISTORY`; `DECISION ≠ DOCUMENTATION OF
DECISION`; `VERSION ≠ REVISION`; `DOCUMENTED ≠ VALIDATED`;
`TRACEABLE ≠ CORRECT`. Documentar no prueba corrección; trazar no
prueba corrección; fuente ≠ interpretación; referencia ≠ evidencia.

## Régimen vinculante de excepciones

Aplica a todos los campos Excepción de estas Rules. Excepción formal
subordinada al régimen C01–C06: alcance determinado, condiciones,
duración cuando corresponda, autoridad competente, autorización
válida, evidencia, revisión y precedencia. Nunca: bypass de
trazabilidad, validación, integridad o seguridad; nueva categoría de
autorización; autoridad implícita. `C04+` indica autoridad mínima,
no permiso genérico para suspender obligaciones.

## R-DT-001 — Mínima documentación necesaria

ID R-DT-001. Nombre: Mínima documentación necesaria. Propósito:
documentar lo necesario para comprender y reconstruir, por niveles
TRIVIAL/LOW/RELEVANT/HIGH/CRITICAL (importancia, impacto,
complejidad, riesgo, permanencia, reconstrucción futura). Alcance:
toda actividad documentable. Categoría RC-09. Obligatoriedad MUST.
Severidad MEDIUM. Condición: cuando la información sea relevante
por impacto, riesgo, permanencia, necesidad de reconstrucción o
función en el flujo —incluida información temporal que participe
en decisiones, validaciones, errores, recuperación, autorización,
cambios relevantes, transiciones de estado o evidencia—. Acción: aplicar el nivel proporcional; trivial ≠
decisión arquitectónica/excepción/alto impacto/fallo crítico/
irreversible. Restricción: prohibida burocracia sin justificación y
omisión en lo relevante. Excepción: excepción formal conforme al régimen vinculante C01–C06 (alcance, condiciones, duración, autoridad competente, autorización válida, evidencia, revisión, precedencia); no elimina obligaciones críticas ni crea autoridad. Autoridad:
autoridad competente C01–C06. Precedencia: base RC-09. Dependencias:
P18/P19/P30, R-GB-010. Relación: dosifica R-CK-009/010. Evidencia:
nivel aplicado. Versión v0.1. Estado PROPOSED. Revisión: triggers
F0-S7 §21. Historial: inicial.

## R-DT-002 — Cadena de trazabilidad

ID R-DT-002. Nombre: Cadena de trazabilidad. Propósito: modelo
OBJECTIVE→TASK→DECISION→ACTION→MODIFICATION→EVIDENCE→VALIDATION→
RESULT→NEXT STATE (+RULE/AUTHORIZATION/EXCEPTION/ERROR/FAILURE/
RECOVERY/REVIEW/APPROVAL/COMMIT/PR/MERGE/DEPLOYMENT/MEASUREMENT
cuando corresponda; no todo es obligatorio siempre). Alcance: cada
trabajo relevante, proporcional. Categoría RC-09. Obligatoriedad
MUST. Severidad HIGH. Condición: durante y al cierre. Acción:
vincular eslabones aplicables. Restricción: prohibidos eslabones
huérfanos requeridos por el contexto, alcance o Rules aplicables
(suficiente, proporcional, reconstruible y verificable; sin
registrar relaciones irrelevantes). Excepción: excepción formal conforme al régimen vinculante C01–C06 (alcance, condiciones, duración, autoridad competente, autorización válida, evidencia, revisión, precedencia); no elimina obligaciones críticas ni crea autoridad.
Autoridad: autoridad competente C01–C06. Precedencia: especializa
la cadena de traza. Dependencias: R-GB-010, R-CK-010, R-MS-008,
R-TQ-008, R-GH-011, R-SP-010, R-ER-009, R-AH-010, P13. Relación:
generaliza las trazas previas. Evidencia: la cadena (meta). Versión
v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial:
inicial.

## R-DT-003 — Documentación de decisiones

ID R-DT-003. Nombre: Documentación de decisiones. Propósito:
toda decisión relevante reconstruible (CONTEXT→PROBLEM→OPTIONS→
CRITERIA→EVIDENCE→DECISION→AUTHORITY→CONSEQUENCES→REVIEW; ADR
cuando aplique). Alcance: decisiones relevantes. Categoría RC-09.
Obligatoriedad MUST. Severidad HIGH. Condición: al decidir.
Acción: registrar los 9 elementos; ADR solo para arquitectónicas/
estratégicas/fundacionales (no toda decisión menor). Restricción:
prohibido decidir sin registro recuperable en lo relevante.
Excepción: excepción formal conforme al régimen vinculante C01–C06 (alcance, condiciones, duración, autoridad competente, autorización válida, evidencia, revisión, precedencia); no elimina obligaciones críticas ni crea autoridad. Autoridad: autoridad competente C01–C06
(documentar una decisión no concede autoridad para tomarla;
`DECISIÓN ≠ AUTORIZACIÓN`; `DOCUMENTACIÓN DE DECISIÓN ≠
AUTORIDAD PARA DECIDIR`). Precedencia: opera con F0-S7/ADR. Dependencias:
R-GB-002/010, P06/P18, F0-S7. Relación: complementa ADR-INDEX.
Evidencia: registro de decisión. Versión v0.1. Estado PROPOSED.
Revisión: triggers F0-S7 §21. Historial: inicial.

## R-DT-004 — Documentación de cambios

ID R-DT-004. Nombre: Documentación de cambios. Propósito:
OBJECTIVE→TASK→AUTHORIZED SCOPE→CHANGE→REASON→AUTHORIZATION→
EVIDENCE→VALIDATION por cambio relevante. Alcance: cambios.
Categoría RC-09. Obligatoriedad MUST. Severidad HIGH. Condición: al
modificar. Acción: vincular eslabones con razón explícita.
Restricción: prohibido justificar retrospectivamente lo no
autorizado. Excepción: excepción formal conforme al régimen vinculante C01–C06 (alcance, condiciones, duración, autoridad competente, autorización válida, evidencia, revisión, precedencia); no elimina obligaciones críticas ni crea autoridad. Autoridad: autoridad
competente. Precedencia: especializa R-MS-008/R-GH-011.
Dependencias: R-MS-008, R-GH-001/011, R-SP-001, P05. Relación:
extiende R-MS-008. Evidencia: cadena del cambio. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-DT-005 — Documentación de validación

ID R-DT-005. Nombre: Documentación de validación. Propósito:
qué/criterio/cuándo/ejecutor/observado/evidencia/desviaciones/
decisión posterior. Alcance: cada validación. Categoría RC-09.
Obligatoriedad MUST. Severidad HIGH. Condición: al validar. Acción:
registrar los 8 elementos (`TEST RESULT ≠ VALIDATION ≠
CERTIFICATION`). Restricción: toda validación relevante
reconstruible con evidencia suficiente; triviales con registro
proporcional. Excepción: excepción formal conforme al régimen vinculante C01–C06 (alcance, condiciones, duración, autoridad competente, autorización válida, evidencia, revisión, precedencia); no elimina obligaciones críticas ni crea autoridad. Autoridad: quien valida
(autoridad competente C01–C06). Precedencia:
especializa R-TQ-006/008. Dependencias: R-TQ-002/006/008, P03.
Relación: complementa R-TQ. Evidencia: registro de validación.
Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21.
Historial: inicial.

## R-DT-006 — Documentación de errores y recuperación

ID R-DT-006. Nombre: Documentación de errores y recuperación.
Propósito: EVENT→DETECTION→CLASSIFICATION→EVIDENCE→DIAGNOSIS→
ACTION→RECOVERY→VALIDATION→RESULT reconstruible (F1-S8).
Alcance: errores/fallos/recuperaciones relevantes. Categoría RC-09.
Obligatoriedad MUST. Severidad HIGH. Condición: al fallar y
recuperar. Acción: registrar la cadena sin ocultar el fallo tras el
estado final. Restricción: prohibido presentar solo el estado final.
Excepción: excepción formal conforme al régimen vinculante C01–C06 (alcance, condiciones, duración, autoridad competente, autorización válida, evidencia, revisión, precedencia); no elimina obligaciones críticas ni crea autoridad. Autoridad: quien ejecuta/recupera.
Precedencia: especializa R-ER-009. Dependencias: R-ER-003/005/009,
P14. Relación: complementa R-ER-009. Evidencia: cadena del
incidente. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7
§21. Historial: inicial.

## R-DT-007 — Documentación de autorizaciones y autonomía

ID R-DT-007. Nombre: Documentación de autorizaciones y autonomía.
Propósito: acción/alcance/autoridad/autorización/condiciones/
duración/evidencia/estado/revocación/expiración identificables.
Alcance: actos con autorización explícita y autonomía concedida.
Categoría RC-09. Obligatoriedad MUST. Severidad HIGH. Condición: al
autorizar y actuar. Acción: registrar los 10 elementos (documenta y
traza los modelos F1-S7/F1-S9 sin reemplazarlos ni crear niveles).
Restricción: prohibido actuar con autorización indocumentada en lo
relevante. Excepción: excepción formal conforme al régimen vinculante C01–C06 (alcance, condiciones, duración, autoridad competente, autorización válida, evidencia, revisión, precedencia); no elimina obligaciones críticas ni crea autoridad. Autoridad: autoridad competente
C01–C06 (documentar una autorización no la concede;
`DOCUMENTAR AUTORIZACIÓN ≠ CONCEDER AUTORIZACIÓN`).
Precedencia: especializa R-SP-010/R-AH-010. Dependencias: R-SP-010,
R-AH-010, P09. Relación: complementa ambas. Evidencia: registro de
autorización. Versión v0.1. Estado PROPOSED. Revisión: triggers
F0-S7 §21. Historial: inicial.

## R-DT-008 — Versionado, obsolescencia e historial

ID R-DT-008. Nombre: Versionado, obsolescencia e historial.
Propósito: estados CURRENT/PROPOSED/SUPERSEDED/DEPRECATED/OBSOLETE/
ARCHIVED; `CURRENT VERSION ≠ COMPLETE HISTORY`; sin sobrescritura
silenciosa; sustituciones con vínculo explícito. Alcance:
documentos, decisiones, conocimiento versionable. Categoría RC-09.
Obligatoriedad MUST. Severidad HIGH. Condición: al versionar o
detectar obsolescencia. Acción: versionar, marcar obsoleto y
vincular sustitución. Restricción: prohibida la sustitución muda de
historial relevante. Excepción: excepción formal conforme al régimen vinculante C01–C06 (alcance, condiciones, duración, autoridad competente, autorización válida, evidencia, revisión, precedencia); no elimina obligaciones críticas ni crea autoridad. Autoridad: autoridad
competente. Precedencia: especializa R-CK-005. Dependencias:
R-CK-005, P19. Relación: opera R-CK-005. Evidencia: versiones +
vínculos. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7
§21. Historial: inicial.

## R-DT-009 — Fuentes, referencias y contradicciones

ID R-DT-009. Nombre: Fuentes, referencias y contradicciones.
Propósito: cadena SOURCE→INFORMATION→INTERPRETATION→DECISION;
referencia localizable; referencia rota/ambigua/inexistente/
desactualizada = condición documental (escalar si afecta decisión,
validación o resultado); sin fuentes inventadas ni retrospectivas.
Alcance: referencias relevantes. Categoría RC-09. Obligatoriedad
MUST. Severidad MEDIUM. Condición: al referenciar. Acción:
verificar localizabilidad y vigencia; tratar contradicciones
(DETECT→PRESERVE→VERSIONS→AUTHORITY→ESCALATE→RESOLVE→DOCUMENT)
sin eliminar documentos para ocultarlas. Restricción: prohibidas
referencias inventadas y eliminaciones silenciosas. Excepción: excepción formal conforme al régimen vinculante C01–C06 (alcance, condiciones, duración, autoridad competente, autorización válida, evidencia, revisión, precedencia); no elimina obligaciones críticas ni crea autoridad. Autoridad: autoridad competente. Precedencia: opera con
RC-02. Dependencias: R-CK-004/006/007, P06. Relación: complementa
R-CK-004/007. Evidencia: referencias verificadas. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-DT-010 — Ubicación, continuidad, responsabilidad y aprendizaje

ID R-DT-010. Nombre: Ubicación, continuidad, responsabilidad y
aprendizaje. Propósito: sin duplicación innecesaria; nada crítico
solo en conversaciones, memoria implícita o ubicación impermanente;
conocimiento relevante fuera de sesión (`DOCUMENTATION ≠ SESSION
MEMORY`); responsabilidad ligada a la actividad (ejecuta/decide/
revisa/valida/certifica/autoriza); obligaciones de futuros agentes
(identificar, documentar, preservar, referenciar, versionar, evitar
implícito, señalar incertidumbre, trazar, no inventar registros);
aprendizaje EXPERIENCE→EVIDENCE→KNOWLEDGE→DOCUMENTATION→VERSION→
REUSE→LEARNING sin auto-cambio normativo (gobierno F1-S1/F0-S7).
Alcance: conocimiento y continuidad. Categoría RC-09.
Obligatoriedad MUST. Severidad HIGH. Condición: cuando exista conocimiento, información, decisión, evidencia, responsabilidad, estado o aprendizaje que deba conservarse, localizarse, atribuirse o reutilizarse para asegurar continuidad o reconstrucción, con proporcionalidad al contexto. Acción:
ubicar, asignar responsable y mantener recuperable, cada obligación
con su alcance claro y proporcionalidad aplicable. Restricción:
prohibidos almacenamiento indiscriminado y registros retrospectivos
inventados. Excepción: excepción formal conforme al régimen vinculante C01–C06 (alcance, condiciones, duración, autoridad competente, autorización válida, evidencia, revisión, precedencia); no elimina obligaciones críticas ni crea autoridad. Autoridad: autoridad
competente. Precedencia: especializa R-CK-009/010. Dependencias:
R-CK-009/010, R-AH-011, P18/P30. Relación: opera R-CK-009/010.
Evidencia: ubicación + responsable. Versión v0.1. Estado PROPOSED.
Revisión: triggers F0-S7 §21. Historial: inicial.
