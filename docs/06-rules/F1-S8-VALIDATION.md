# F1-S8-VALIDATION — Matriz de aceptación RC-07

Sprint: F1-S8. Fecha: 2026-09-30. Versión: v0.1. Estado:
READY_FOR_REVIEW (no CERTIFIED/APPROVED/ACTIVE/COMPLETED). Creados:
`docs/06-rules/F1-S8-RULES-ERRORS-RECOVERY-ESCALATION.md`,
`docs/06-rules/F1-S8-VALIDATION.md`. Modificados: ninguno.
Rules: 9 (R-ER-001…R-ER-009), RC-07, PROPOSED v0.1.

## Estructura — PASS

Serie `R-ER-NNN` (taxonomía RC-07 confirmada), 20/20 campos
explícitos por Rule, RC-07 exclusiva, MUST ×9, severidades
CRITICAL×1/HIGH×7/MEDIUM×1, PROPOSED. Sin contrato alternativo.

## Dependencias — PASS

F1-S1 (contrato/lifecycle/precedencia), F1-S2 (transparencia/stop/
escalado/evidencia), F1-S3 (incertidumbre/traza), F1-S4 (alcance/
STOP/secuencia), F1-S5 (validación/evidencia/VALIDATED), F1-S6
(responsabilidades/autorización), F1-S7 (autorización/excepciones);
P01–P26 citados; F0-S5/S7 intactos.

## Coherencia — PASS

0 contradicciones; 0 duplicaciones (R-GB-007/008/009, R-MS-007,
R-TQ-003, R-SP-004/007 especializadas con Relación declarada);
precedencia declarada; autoridad C04 sin técnica nueva; STOP
consistente; escalamiento consistente; validación consistente.

## Distinciones — PASS (10/10)

ERROR/FAILURE, FAILURE/BLOCKED, BLOCKED/RECOVERING,
RECOVERING/SUCCESS, RETRY/RECOVERY, RECOVERY/VALIDATION,
VALIDATION/CERTIFICATION, EVIDENCE/VALIDATION, STOP/CANCEL,
ESCALATION/FAILURE — todas en §Distinciones + Rules.

## Seguridad — PASS

0 autorización implícita; 0 recovery fuera de alcance (R-ER-005 con
alcance/autoridad); escalamiento no sustituye validación (R-ER-007
+ R-ER-008); 0 retry infinito/ciego (R-ER-004 límites); 0
continuación insegura (R-ER-002/008).

## Cobertura — PASS (20/20)

Q1/Q2→001 Q3→002 Q4→003 Q5→001 Q6/Q7→004 Q8→005 Q9→005 Q10→005/008
Q11→008 Q12→008 Q13→007 Q14→007 Q15→005 (rollback=técnica)
Q16→003 Q17→001/002 Q18→001 (BLOCKED) Q19→004 Q20→009.

## Alcance — PASS

0 implementación (automática/observabilidad/alertas/infra/código) ;
0 OpenCode/runtime normativo; 0 Orchestrator/Agents/Skills.

## Integridad — PASS

`git diff --check`: limpio. `git status`: rama `operativo` + 2
untracked autorizados; F1-S1…S7 intactos. Greps: 9/9 IDs,
0 ACTIVE/APPROVED/CERTIFIED, 0 mecanismos técnicos.

## Refinamiento R1 — aplicado

Motivo: coherencia normativa tras revisión independiente, previo a
revisión humana. Cambios: R-ER-001 (BLOCKED ≠ STOP separados);
R-ER-003 (evidencia parcial explícita y trazable); R-ER-005
(RECOVERY normativo, ROLLBACK técnica futura); R-ER-007
(escalamiento sin agotar vía cuando falta base); R-ER-009
(trazabilidad proporcional; excepción ≠ huérfano); convenciones:
límites de excepción formal + régimen C01–C06 (AUTHORITY ≠
APPROVAL ≠ AUTHORIZATION). Alcance: F1-S8 únicamente. Archivos
fuera de alcance modificados: ninguno. Revalidación: estructura
9 Rules/20 campos/PROPOSED; dependencias F1-S1…S7; 10/10
distinciones; retry/recovery/stop/escalado/excepciones/traza
verificados; Q1–Q20 20/20 (Q15→005, Q13/14→007 sin exigir
agotamiento); regresión F1-S1…S7 intactos; scope 0 técnico;
`git diff --check` limpio.
