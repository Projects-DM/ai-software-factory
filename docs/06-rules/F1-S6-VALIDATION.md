# F1-S6-VALIDATION — Matriz de aceptación RC-05

Sprint: F1-S6. Fecha: 2026-09-30. Versión: v0.1. Estado:
READY_FOR_REVIEW (no CERTIFIED). Creados:
`docs/06-rules/F1-S6-RULES-GIT-GITHUB.md`,
`docs/06-rules/F1-S6-VALIDATION.md`. Modificados: ninguno.
Rules: 12 (R-GH-001…R-GH-012), RC-05, PROPOSED v0.1.

## Estructura/Contrato — PASS (tras corrección)

`docs/06-rules/`, serie `R-GH-NNN`, RC-05 exclusiva, MUST (+MUST NOT
R-GH-010), severidades MEDIUM/HIGH/CRITICAL, PROPOSED. Corrección
aplicada: cada Rule R-GH-001…012 incluye línea `Contrato:` explícita
con Categoría, Autoridad, Precedencia, Dependencias, Relación,
Revisión e Historial (+13 campos ya en ficha = 20/20 verificable por
Rule). Convenciones comunes permanecen como apoyo con referencia
inequívoca. Sin cambio de significado, alcance ni Rules.

## Dependencias — PASS

F1-S1 (contrato/gobernanza), F1-S2 (alcance/preservación/validación/
stop/escalado/evidencia/traza especializadas), F1-S3 (contexto/
vigencia/traza), F1-S4 (alcance/cambios/STOP/trazabilidad),
F1-S5 (validación/evidencia/VALIDATED/CERTIFIED); P03–P26 citados.

## Coherencia — PASS

0 contradicciones; 0 duplicaciones injustificadas (traza/validación/
stop referencian y especializan); precedencia declarada; autoridad
C04 sin técnica nueva; GitHub nunca autoridad normativa;
distinciones §7 íntegras (incl. GIT≠GITHUB, PUSH≠MERGE,
MERGE≠DEPLOYMENT).

## Alcance — PASS

Normativo portable; 0 implementación (Actions/CI-CD/APIs/webhooks/
permisos/credenciales/infra/despliegues/SGC-DM ausentes);
0 dependencia OpenCode; `main` conceptual sin branch protection.

## Cobertura — PASS (20/20)

Q1 R-GH-001 | Q2 R-GH-002 | Q3–Q5 R-GH-003 | Q6 R-GH-004 | Q7 R-GH-005 |
Q8 R-GH-006 | Q9 R-GH-007 | Q10 R-GH-001/011 | Q11 R-GH-009 | Q12 R-GH-008 |
Q13/Q14/Q15/Q20 R-GH-010 (+006/007) | Q16 R-GH-006/011 | Q17 R-GH-006/011 |
Q18/Q19 R-GH-012 | Q17-verificación-post-merge R-GH-006/007/011.

## Evidencia — PASS

`git diff --check`: limpio. `git status`: rama `operativo` + 2
untracked autorizados; F0/F1-S1…S5 intactos. Greps: 12/12 IDs,
0 ACTIVE, 0 autorizaciones implícitas, 0 herramientas/Actions,
0 ramas del repo convertidas en política.
