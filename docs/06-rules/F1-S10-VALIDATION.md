# F1-S10-VALIDATION — Matriz de aceptación RC-09

Sprint: F1-S10 (+ refinamientos R1, R1.1). Fecha: 2026-09-30. Versión:
v0.1. Estado:
READY_FOR_HUMAN_REVIEW (no APPROVED/ACTIVE/CERTIFIED).
Archivos de F1-S10:
- Creados en el sprint:
  - `docs/06-rules/F1-S10-RULES-DOCUMENTATION-TRACEABILITY.md`
  - `docs/06-rules/F1-S10-VALIDATION.md`
- Refinados/modificados durante F1-S10 (R1, R1.1):
  - `docs/06-rules/F1-S10-RULES-DOCUMENTATION-TRACEABILITY.md`
  - `docs/06-rules/F1-S10-VALIDATION.md`
- Archivos fuera del alcance modificados:
  - ninguno.
Rules: 10 (R-DT-001…R-DT-010), RC-09, PROPOSED v0.1.

## Estructura — PASS

Serie `R-DT-NNN`, RC-09 exclusiva, 20/20 explícitos por Rule, MUST
×10, severidades MEDIUM×2/HIGH×8, PROPOSED. Sin contrato
alternativo ni campos agregados.

## Cobertura Q01–Q26 — PASS (26/26, derivadas del spec §§4,7–22+26)

Q01→001 Q02→001 Q03→010 Q04→001 Q05→010 Q06→002 Q07→002 Q08→002
Q09→003 Q10→003 Q11→004 Q12→004 Q13→005 Q14→005 Q15→006 Q16→006
Q17→007 Q18→007 Q19→008 Q20→008 Q21→008 Q22→009 Q23→009 Q24→010
Q25→010 Q26→010. Q01–Q26 forman parte de la especificación de
entrada y se usan como criterios de cobertura con correspondencia
verificable por Rule (26/26).

## Dependencias — PASS

F1-S1 (contrato), F1-S2 (conducta/evidencia), F1-S3
(contexto/preservación/traza), F1-S4 (cambios/alcance), F1-S5
(validación), F1-S6 (Git/PR/traza), F1-S7 (autorización), F1-S8
(errores/traza), F1-S9 (autonomía/intervención); P01–P30 citados.

## Distinciones — PASS (13/13 §7 + corolarios).

## Seguridad y gobernanza — PASS

0 autorización implícita/ampliada; 0 niveles C/autonomía nuevos;
0 bypass de gates; 0 memoria implícita como base; 0 legitimación
retrospectiva; 0 eliminación silenciosa; 0 implementación técnica.

## Proporcionalidad — PASS

Niveles TRIVIAL…CRITICAL; R-DT-001/002/010 exigen proporcionalidad;
sin burocracia injustificada.

## Regresión — PASS

F1-S1…S9 intactos (solo 2 untracked nuevos).

## Integridad — PASS

`git diff --check`: limpio. `git status`: rama `operativo` + 2
untracked autorizados. Greps: 10/10 IDs, 0 ACTIVE/APPROVED/
CERTIFIED, 0 mecanismos técnicos.

## Refinamiento R1 — aplicado

Excepciones subordinadas a C01–C06 (sección vinculante; sin bypass
ni nueva categoría); R-DT-001 condición por relevancia (incluye
temporal relevante); R-DT-002 huérfanos requeridos por contexto/
alcance/Rules; R-DT-003/007 autoridad competente C01–C06
(documentar ≠ conceder); R-DT-005 validación relevante
reconstruible; R-DT-010 unificada y proporcional. Q01–Q26 como
criterios de entrada (26/26). Estado: READY_FOR_HUMAN_REVIEW.

## Refinamiento R1.1 — aplicado

Excepciones normalizadas 10/10 al régimen vinculante (sin excepción especial C01 en R-DT-002); R-DT-010 con condición contextual (no absoluta) y unidad conservada; validación con trazabilidad factual de archivos (creados/refinados/fuera de alcance). Sin nuevas Rules, sin cambio de alcance, sin implementación. Estado: READY_FOR_HUMAN_REVIEW.
