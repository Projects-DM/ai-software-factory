# F1-S5-VALIDATION — Matriz de aceptación RC-04

Sprint: F1-S5. Fecha: 2026-09-30. Versión: v0.1. Estado:
READY_FOR_REVIEW (no CERTIFIED). Creados:
`docs/06-rules/F1-S5-RULES-TESTING-QUALITY.md`,
`docs/06-rules/F1-S5-VALIDATION.md`. Modificados: ninguno.
Rules: 8 (R-TQ-001…R-TQ-008), RC-04, PROPOSED v0.1.

## Estructura — PASS

`docs/06-rules/`, nomenclatura `R-TQ-NNN`, 20 campos (ficha +
convenciones comunes), RC-04 exclusiva, MUST (+HUMAN APPROVAL
heredado de gates), severidades CRITICAL/HIGH/MEDIUM, PROPOSED.

## Contrato — PASS

20/20 campos por Rule; sin contrato alternativo; sin campos
agregados; estados y versionado F1-S1.

## Dependencias — PASS

F1-S1 (contrato/gobernanza), F1-S2 (R-GB-006/007/008/009/010
especializadas), F1-S3 (R-CK-004/005), F1-S4 (R-MS-004/007/008);
P03–P30 citados; F0-S5/S7 intactos.

## Coherencia — PASS

0 contradicciones; 0 duplicaciones injustificadas (R-GB-006
general → R-TQ mecánica; R-MS-007 secuencia → R-TQ-003
consecuencias); precedencia declarada; autoridad C04 sin técnica
nueva; STOP/PRESERVE/ESCALATE/WAIT/CONTINUE coherentes.

## Alcance — PASS

Normativo, sin testing implementado ni frameworks (0 menciones:
Jest/Vitest/Playwright/Cypress/pytest), sin Agents/Skills/
Orchestrator/CI-CD/permisos/producción/SGC-DM; factory terms,
runtime independence verificada (0 menciones OpenCode como
requisito).

## Cobertura — PASS (15/15)

Q1 R-TQ cadena+IMPLEMENTED | Q2 R-TQ-001/002 | Q3 distinciones+R-TQ-002 |
Q4/Q5 R-TQ-003 (NOT EXECUTED/FAILED) | Q6 R-TQ-002/003 | Q7 R-TQ-005 |
Q8 R-TQ-004 | Q9/Q10 R-TQ-006 | Q11/Q12 R-TQ-003/007 | Q13 R-TQ-001 |
Q14 R-TQ-007 | Q15 R-TQ-008.

## Evidencia — PASS

`git diff --check`: limpio. `git status`: rama `operativo` + 2
untracked autorizados; F0/F1-S1…S4 intactos. Greps: 8/8 IDs,
0 ACTIVE, 0 autorizaciones implícitas, 0 herramientas concretas.
