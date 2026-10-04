# F1-S12-RULES-GOVERNANCE-EVOLUTION — Rules de gobierno y evolución de Rules

Fase: F1 — Rules. Sprint: F1-S12. Categoría: RC-11 (Governance /
Evolution). Serie `R-GE-NNN` (formato `R-<CAT>-<NNN>` F1-S1).
Todas: PROPOSED v0.1 — definidas ≠ aprobadas ≠ activas. Cada Rule
contiene explícitos sus 20 campos F1-S1. Meta-categoría: gobierna
las Rules sin reescribir F1-S1…S11. Sin rule engine, automatización,
CI/CD, dashboards ni código. Principio: `RULES MAY EVOLVE BUT RULE
EVOLUTION IS GOVERNED`; `CAPABILITY TO MODIFY RULE ≠ AUTHORIZATION
TO MODIFY RULE`.

## Distinciones (§6)

`PROPOSAL ≠ APPROVAL ≠ ACTIVATION ≠ IMPLEMENTATION ≠ VALIDATION ≠
CERTIFICATION`; `VERSION ≠ REVISION ≠ REPLACEMENT ≠ DEPRECATION ≠
REMOVAL`; `EXCEPTION ≠ RULE CHANGE ≠ RULE BYPASS`; `FEEDBACK ≠
EVIDENCE ≠ DECISION`; `AUTOMATION ≠ AUTHORITY`; `CAPABILITY ≠
AUTHORIZATION`. Lifecycle F1-S1 vigente; transiciones
CURRENT→CONDITION→EVIDENCE→AUTHORITY→DECISION→NEW STATE.

## R-GE-001 — Propuesta legítima

ID R-GE-001. Nombre: Propuesta legítima. Propósito: cualquiera
(incluido un agente: detectar, proponer, analizar, evidenciar)
puede proponer; proponer no autoriza (Q1). Alcance: propuestas
normativas. Categoría RC-11. Obligatoriedad MUST. Severidad HIGH.
Condición: al proponer. Acción: registrar problema, objetivo,
propuesta y evidencia inicial con autor identificado. Restricción:
prohibido proponer sin fundamento o auto-aprobarse (el agente no
aprueba lo propio). Excepción: no aplica (acto previo a la norma).
Autoridad: proponer, cualquiera con capacidad de formular; admitir,
revisar, aprobar y activar, solo las autoridades correspondientes
según C01–C06 y condiciones (proponer no concede nada). Precedencia:
base RC-11. Dependencias: R-GB-002, P06. Relación: puerta de
R-GE-002. Evidencia: propuesta registrada. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-GE-002 — Revisión proporcional

ID R-GE-002. Nombre: Revisión proporcional. Propósito: profundidad
∝ impacto/riesgo/alcance/sensibilidad/reversibilidad/incertidumbre
(Q2, Q7). Alcance: pre-aprobación. Categoría RC-11. Obligatoriedad MUST. Severidad HIGH. Condición: propuesta admitida. Acción:
revisar con separación proponente/revisor y registrar veredicto.
Restricción: prohibido aprobar sin revisión ni revisar
superficialmente lo crítico. Excepción: solo formal subordinada
(C01–C06, alcance, impacto, autoridad, autorización, condiciones,
duración, evidencia, revisión, precedencia); C04+ no es excepción
automática ni elimina controles, evidencia o historia. Autoridad:
revisor competente C01–C06. Precedencia: opera con F0-S7.
Dependencias: R-GE-001, P03/P25. Relación: consume R-GE-001.
Evidencia: veredicto + alcance revisado. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-GE-003 — Aprobación con autoridad explícita

ID R-GE-003. Nombre: Aprobación con autoridad explícita. Propósito:
aprueba quien tenga nivel competente (alto impacto: humano); el
proponente-agente jamás aprueba lo propio (Q3). Alcance:
aprobación. Categoría RC-11. Obligatoriedad MUST. Severidad CRITICAL. Condición: revisión superada. Acción: aprobar con
autoridad, alcance y condiciones registradas. Restricción:
prohibidas auto-aprobación y aprobación fuera de nivel. Excepción:
ninguna para la exigencia. Autoridad: autoridad competente conforme al régimen C01–C06, considerando alcance, impacto, sensibilidad, condiciones, precedencia y demás criterios aplicables; cuando las Rules o el impacto requieran intervención humana, la aprobación pasa por el Human Gate correspondiente. Precedencia: base RC-11. Dependencias: R-GE-002,
R-SP-003, P02/P09. Relación: consume R-GE-002. Evidencia: acto de
aprobación. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7
§21. Historial: inicial.

## R-GE-004 — Activación condicionada

ID R-GE-004. Nombre: Activación condicionada. Propósito:
`APPROVAL ≠ ACTIVATION`: activar exige condiciones cumplidas,
evidencia y fecha de vigencia (Q4, Q8). Alcance: puesta en vigor.
Categoría RC-11. Obligatoriedad MUST. Severidad HIGH. Condición:
aprobación vigente + condiciones. Acción: activar con registro y
fecha; sin condiciones no hay vigencia (evita el ciclo
aprobación↔activación: la activación sigue causal y
temporalmente a la aprobación). Restricción: prohibido operar
reglas no activas. Excepción: solo formal subordinada (C01–C06,
alcance, impacto, autoridad, autorización, duración, evidencia,
revisión, precedencia); nunca bypass. Autoridad: la competente
conforme a C01–C06, alcance, impacto, sensibilidad, condiciones y
precedencia (aprobar no implica activar; quien aprobó no activa
automáticamente). Precedencia: opera con lifecycle F1-S1.
Dependencias: R-GE-003, P03. Relación: consume R-GE-003.
Evidencia: activación + vigencia. Versión v0.1. Estado PROPOSED.
Revisión: triggers F0-S7 §21. Historial: inicial.

## R-GE-005 — Modificación y versionado

ID R-GE-005. Nombre: Modificación y versionado. Propósito: todo
cambio normativo con versión identificable conforme al esquema
normativo adoptado, trazado y nunca
silencioso (Q9, Q10). Alcance: modificaciones. Categoría RC-11.
Obligatoriedad MUST. Severidad HIGH. Condición: al modificar.
Acción: versionar con qué/cómo/quién/vigencia/sustituida/
compatibilidad. Restricción: prohibida edición silenciosa.
Excepción: solo formal subordinada (C01–C06, alcance, impacto,
autoridad, autorización, duración, evidencia, revisión,
precedencia); nunca sobrescritura silenciosa, pérdida de
historial, eliminación de evidencia, cambio retrospectivo ni
omisión de versionado. Autoridad: autoridad competente conforme a C01–C06, considerando alcance, impacto, sensibilidad, condiciones, precedencia y características de la Rule afectada (`CAPABILITY TO EDIT ≠ AUTHORIZATION TO MODIFY`). Precedencia: opera con R-CK-005/R-DT-008. Dependencias: R-CK-005,
R-DT-008, P19. Relación: especializa versionado. Evidencia:
versión + diff normativo. Versión v0.1. Estado PROPOSED. Revisión:
triggers F0-S7 §21. Historial: inicial.

## R-GE-006 — Reemplazo, suspensión, deprecación y retiro

ID R-GE-006. Nombre: Reemplazo, suspensión, deprecación y retiro.
Propósito: `REPLACEMENT ≠ DEPRECATION ≠ REMOVAL`; sustitución con
cadena preservada; retiro mediante decisión explícita y evaluación de impacto, dependencias, referencias, compatibilidad, historial y migración cuando aplique (Q11,
Q12). Alcance: fin de vida. Categoría RC-11. Obligatoriedad MUST.
Severidad HIGH. Condición: al sustituir/retirar. Acción: enlazar la sustituta cuando exista, actualizar o migrar referencias cuando corresponda y comunicar a los afectados cuando resulte aplicable. Restricción: prohibido
retirar sin deprecación ni romper referencias sin migración.
Excepción: solo formal subordinada (C01–C06, alcance, impacto,
autoridad, autorización, duración, evidencia, revisión,
precedencia); el retiro exige decisión explícita tras evaluar
impacto, dependencias, referencias, compatibilidad, historial y
migración cuando aplique (sin migración ficticia si no hay
consumidores). Autoridad: autoridad competente conforme a C01–C06, considerando alcance, impacto, sensibilidad, condiciones, precedencia y características de la Rule afectada. Precedencia: opera con lifecycle F1-S1. Dependencias: R-GE-005,
R-DT-008, P19. Relación: cierra R-GE-005. Evidencia: cadena de
sustitución. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7
§21. Historial: inicial.

## R-GE-007 — Conflictos y dependencias

ID R-GE-007. Nombre: Conflictos y dependencias. Propósito: ante
nueva Rule: REUSE/SPECIALIZE/MODIFY BEFORE CREATE; evaluar
duplicación, contradicciones, precedencia, dependencias e impactos
(autonomía, validación, certificación, documentación, permisos);
conflicto no resuelto por eliminación (Q14–Q17). Alcance:
diseño de Rules. Categoría RC-11. Obligatoriedad MUST. Severidad HIGH. Condición: antes de crear. Acción: análisis previo
registrado. Restricción: prohibido duplicar o contradecir.
Excepción: solo formal subordinada (C01–C06 y régimen); evalúa
también contradicciones, precedencia y dependencias. Autoridad: revisor competente conforme a C01–C06 y condiciones aplicables.
Precedencia: conforme al contrato F1-S1 y a las Rules aplicables según alcance, autoridad, dependencias, contradicción y precedencia. Dependencias: R-GB-011,
P05/P10. Relación: compuerta de creación. Evidencia: análisis.
Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21.
Historial: inicial.

## R-GE-008 — Cambios de alto impacto

ID R-GE-008. Nombre: Cambios de alto impacto. Propósito: lo que
aumenta autonomía, reduce gates, amplía capacidades/permisos,
reduce controles, modifica autoridad, toca seguridad/producción/
destructivas/datos o principios recibe revisión superior y
autoridad correspondiente; nunca se aprueba por productividad
esperada (Q18–Q20). Alcance: lista §13. Categoría RC-11.
Obligatoriedad MUST. Severidad CRITICAL. Condición: al calificar
alto impacto. Acción: elevar revisión y autoridad; registrar.
Restricción: prohibida aprobación ligera. Excepción: ninguna para
la elevación. Autoridad: autoridad competente conforme a C01–C06 y al impacto del cambio; los cambios que afecten autonomía, control humano, seguridad, autoridad, permisos, principios fundamentales o condiciones de alto impacto requieren el Human Gate correspondiente conforme a F1-S9. Precedencia: base
RC-11. Dependencias: R-SP-003/004, R-AH-002, P01/P02. Relación:
consume R-GE-002. Evidencia: revisión superior. Versión v0.1.
Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-GE-009 — Excepciones normativas

ID R-GE-009. Nombre: Excepciones normativas. Propósito:
`EXCEPTION ≠ RULE CHANGE`: 9 campos, temporalidad, revocación/
expiración; jamás bypass permanente, autoridad implícita, fin de
traza/validación, reescritura histórica, nivel C nuevo (Q21, Q23).
Alcance: excepciones. Categoría RC-11. Obligatoriedad MUST.
Severidad HIGH. Condición: al exceptuar. Acción: aplicar régimen
formal completo. Restricción: prohibido convertir excepción en
regla. Excepción: no aplica (régimen de excepciones). Autoridad:
nivel competente conforme a C01–C06 y condiciones aplicables. Precedencia: subordinada al régimen de autoridad, autorización, seguridad, integridad, errores/recuperación y demás Rules aplicables conforme al contrato F1-S1 (sin precedencia automática por categoría). Dependencias:
R-SP (régimen), R-ER-007, P09. Relación: opera el régimen.
Evidencia: registro de excepción. Versión v0.1. Estado PROPOSED.
Revisión: triggers F0-S7 §21. Historial: inicial.

## R-GE-010 — Cambios urgentes

ID R-GE-010. Nombre: Cambios urgentes. Propósito: vía rápida sin
eliminar autoridad, autorización, trazabilidad, evidencia ni
revisión posterior cuando corresponda (Q22). Alcance: urgencia justificada. Categoría RC-11. Obligatoriedad MUST. Severidad HIGH. Condición: daño
inminente o bloqueo crítico documentado. Acción: aplicar mediante autorización competente, preservar evidencia y realizar revisión posterior cuando corresponda conforme al impacto, riesgo, naturaleza del cambio y Rules aplicables (esta puede determinar CONTINUE/MODIFY/REPLACE/REVOKE/SUPERSEDE). Restricción: prohibida urgencia como excusa para
omitir controles. Excepción: la urgencia no exime revisión
posterior cuando corresponda (nunca exime autoridad, autorización,
trazabilidad, evidencia ni controles críticos). Autoridad: competente disponible. Precedencia: subordinada al régimen de autoridad, autorización, seguridad, integridad, errores/recuperación y demás Rules aplicables conforme al contrato F1-S1 (sin precedencia automática por categoría). Dependencias: R-ER-002/007, P14.
Relación: vía excepcional de R-GE-002…004. Evidencia: urgencia +
revisión posterior cuando corresponda. Versión v0.1. Estado PROPOSED. Revisión: triggers
F0-S7 §21. Historial: inicial.

## R-GE-011 — Evolución basada en evidencia

ID R-GE-011. Nombre: Evolución basada en evidencia. Propósito:
resultados, fallos, validaciones, incidentes, métricas, revisiones,
experiencia y cambios arquitectónicos como base legítima cuando
corresponda, junto a necesidades normativas nuevas identificables;
preferencias subjetivas aisladas insuficientes para cambios
críticos; aprendizaje sin auto-modificación (Q24–Q27). Alcance: evolución.
Categoría RC-11. Obligatoriedad MUST. Severidad HIGH. Condición:
ante propuesta de evolución. Acción: exigir base evidencial y
decisión gobernada. Restricción: prohibidos cambios por moda,
opinión o éxito aislado. Excepción: solo formal subordinada
(C01–C06 y régimen). Autoridad: autoridad competente conforme a C01–C06, considerando alcance, impacto, sensibilidad, condiciones, precedencia y demás criterios aplicables. Precedencia: opera con RC-04/11 y P25/P26.
Dependencias: R-TQ-004, R-AH-011, R-DT-010, P20/P25/P26.
Relación: consume R-AH-011. Evidencia: base + decisión. Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7 §21. Historial: inicial.

## R-GE-012 — Trazabilidad y comunicación del cambio

ID R-GE-012. Nombre: Trazabilidad y comunicación del cambio.
Propósito: cadena PROBLEM→OBJECTIVE→PROPOSAL→EVIDENCE→REVIEW→
DECISION→AUTHORITY→VERSION→ACTIVATION→VALIDATION→RESULT +
compatibilidad/migración/comunicación a afectados (Q28–Q30).
Alcance: cada cambio (trazabilidad obligatoria; comunicación proporcional). Categoría RC-11. Obligatoriedad MUST.
Severidad HIGH. Condición: al cambiar. Acción: registrar y vincular el cambio; comunicarlo a las partes afectadas cuando corresponda, con alcance y nivel de detalle proporcionales al impacto y relevancia del cambio. Restricción: prohibidos cambios mudos. Excepción:
solo formal subordinada (C01–C06 y régimen). Autoridad: quien cambia con competencia. Precedencia:
especializa la cadena de traza. Dependencias: R-GB-010, R-DT-002/
008, P13. Relación: extiende R-DT-002/008. Evidencia: la cadena
(meta). Versión v0.1. Estado PROPOSED. Revisión: triggers F0-S7
§21. Historial: inicial.
