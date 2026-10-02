# F1-S7-VALIDATION — Matriz de aceptación RC-06

Sprint: F1-S7 (+ refinamiento F1-S7-R). Fecha: 2026-09-30. Versión:
v0.1. Estado:
READY_FOR_REVIEW (no CERTIFIED/APPROVED/ACTIVE/COMPLETED).
Archivos de F1-S7:
- Creados en el sprint:
  - `docs/06-rules/F1-S7-RULES-SECURITY-PERMISSIONS.md`
  - `docs/06-rules/F1-S7-VALIDATION.md`
- Refinados/modificados durante F1-S7 (R, R2, R3, R4):
  - `docs/06-rules/F1-S7-RULES-SECURITY-PERMISSIONS.md`
  - `docs/06-rules/F1-S7-VALIDATION.md`
- Archivos fuera del alcance modificados:
  - ninguno.
Rules: 12 (R-SP-001…R-SP-012), RC-06, PROPOSED v0.1.

## Estructura/Contrato — PASS

Serie `R-SP-NNN`, RC-06 exclusiva, 20/20 campos explícitos por Rule
(inline, lección F1-S6), MUST ×12 (prohibiciones vía campo
Restricción), severidades CRITICAL×2/HIGH×9/MEDIUM×1, PROPOSED. Sin
contrato alternativo.

## Dependencias — PASS

F1-S1 (contrato/gobernanza/lifecycle/precedencia), F1-S2 (límites/
evidencia/stop/escalado), F1-S3 (contexto/vigencia/traza), F1-S4
(scope/cambios/escalado), F1-S5 (validación/evidencia/VALIDATED),
F1-S6 (responsabilidades Git/autorización); P01/P02/P05/P06/P09/
P10/P12/P13/P14/P17–P19/P23/P24/P26/P29.

## Coherencia — PASS (revalidada tras F1-S7-R)

0 contradicciones; 0 duplicaciones (F1-S3 complementado en R-SP-012;
R-GB-004 gemelada en R-SP-011; traza extendida en R-SP-010);
precedencia declarada; autoridad C04 sin técnica nueva; GitHub nunca
autoridad; distinciones §8 íntegras. Pares verificados: R-SP-001↔003
(rutina autónoma vs tiers), 003↔F0 Governance (C01–C06 exactos),
007↔008 (insuficiente vs excesivo), 001↔P01/P02, 002↔LP, 005↔Auth,
006↔revocación, 009↔precedencia, 010↔traza, 011↔SoR, 012↔acceso.
Autonomía: rutina+alcance→autonomía; sensible→autorización explícita;
fuera de alcance→STOP/ESCALATE/WAIT; prohibido→no ejecutar.

## Refinamiento F1-S7-R — aplicado

R-SP-001: rutina autónoma sin nueva aprobación vs autorización
explícita adicional vs STOP vs no-ejecutar. R-SP-003: C01–C06 de
gobernanza F0 (sin jerarquía nueva); autoridad solo en ámbito
legítimo. R-SP-007: cobertura completa de los supuestos de insuficiencia, incertidumbre, falta de autorización, expiración/revocación y solicitudes fuera del alcance conocido; exceso de privilegio separado en R-SP-008.
R-SP-008: intacta (función exceso-privilegio). 12 Rules, 20 campos,
PROPOSED, sin cambio de alcance de F1-S7; se realizaron ajustes
semánticos y de precisión normativa para eliminar ambigüedades
detectadas durante la revisión independiente (sin nueva Rule, sin
cambio de arquitectura).

## Refinamiento F1-S7-R2 — aplicado

R-SP-001: eliminada la ambigüedad "cada acto exige su autorización";
rutina autorizada → autonomía sin nueva aprobación; autorización
válida distinguida de evidencia (pre-acto: AUTHORIZATION+SCOPE+
CONDITIONS+LEAST PRIVILEGE; durante/después: ACTION→EVIDENCE→
VALIDATION→RESULT); sensibles → autorización explícita adicional;
fuera de alcance → STOP; prohibido → no ejecutar. R-SP-003/007/008
sin cambios (verificada coherencia con R-SP-001 corregida).

## Alcance — PASS

Normativo; 0 implementación (autenticación/RBAC/secretos/IAM/cifrado/
infra/Agents/Skills/Orchestrator/automatización/CI-CD/SGC-DM
ausentes); portable; runtime independence (0 OpenCode normativo).

## Cobertura — PASS (20/20)

Q1→001 Q2→001 Q3→002 Q4→003 Q5→003/004 Q6→003+C-niveles Q7→003/005
Q8→005 Q9→006 Q10→006 Q11→007 Q12→007 Q13→008 Q14→004/003 Q15→011
Q16→010 Q17→010 Q18→campos Excepción + §16 F1-S1 Q19→004/007 Q20→001.

## Evidencia — PASS

`git diff --check`: limpio. `git status`: rama `operativo` + 2
untracked autorizados; F0/F1-S1…S6 intactos. Greps: 12/12 IDs,
0 ACTIVE/APPROVED/CERTIFIED, 0 autorizaciones implícitas
("si puede hacerlo, puede hacerlo": 0), 7 etapas separadas
presentes, 0 herramientas/credenciales.
