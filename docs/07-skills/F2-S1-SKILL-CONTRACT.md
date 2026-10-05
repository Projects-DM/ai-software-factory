# F2-S1-SKILL-CONTRACT — Definición y contrato estándar de Skill

Fase: F2 — Skills. Sprint: F2-S1 — Definition and Skill Contract.
Estado: CONTRACT PROPOSED v0.1 (no aprobado, no activo). Sin Skills
funcionales, Agents, Orchestrator, Runtime Adapter ni automatización.
Base normativa: F0, F1 (Rules vigentes), auditoría RUNTIME-DECOUPLING
(REC-01: formato Factory-native). F2-00 no localizado en el
repositorio — gap documentado en validación; no se inventa su
contenido.

## 1. Definición: SKILL = REUSABLE ENGINEERING CAPABILITY

Capacidad de ingeniería reutilizable ejecutable por un Agent
autorizado bajo Rules y autorizaciones. NO es: Rule, Agent, Runtime,
herramienta, tecnología, tarea, proyecto, autorización, memoria o
contexto privados de sesión/agente, ni personalidad.

## 2. Distinciones (§6)

`RULE ≠ SKILL` (permitido vs procedimiento), `SKILL ≠ AGENT`
(capacidad vs responsabilidad/ejecución), `AGENT ≠ RUNTIME`,
`RUNTIME ≠ TOOL`, `CAPABILITY ≠ TECHNOLOGY`, `SKILL ≠ TASK ≠
PROJECT ≠ AUTHORIZATION`, `CAPABILITY ≠ AUTHORIZATION`,
`AUTHORITY ≠ AUTHORIZATION`, `PERMISSION ≠ EXECUTION`,
`EXECUTION ≠ SUCCESS ≠ VALIDATION`, `EVIDENCE ≠ VALIDATION ≠
CERTIFICATION`, `SKILL ≠ AGENT MEMORY`, `KNOWLEDGE ≠ SESSION
CONTEXT`.

## 3. Independencias (§§7–9)

- Agent: `Skill → capability/procedure`, `Agent →
  responsibility/orchestration/execution`. Sin identidad, memoria,
  personalidad, autoridad, permisos ni estado de Agent. A/B/C la usan
  si tienen capacidad, contexto, herramientas, autorización y alcance.
- Runtime: Factory Rules/Skills/Knowledge → Agent Contract →
  Runtime Adapter (FUTURO, no implementado aquí) → OpenCode/B/C →
  Tools. OpenCode primer runtime, nunca propietario; `.opencode/
  skills/` es adaptación, no norma.
- Tecnología: `CAPABILITY → SKILL → TECHNOLOGY` (Database
  Engineering → Relational → PostgreSQL/MySQL/MariaDB). Ninguna
  tecnología redefine la capacidad.

## 4. Contrato de 18 campos (§10)

Formato: campo — contenido exigible.

1. **ID** — único estable (`SK-<DOMINIO>-<NNN>`); inmutable tras
   aprobación. 2. **Name** — breve, sin jerga de producto ni runtime.
3. **Version** — `vMAYOR.menor` + cambios/motivo/impacto/
   compatibilidad/historial. 4. **Purpose** — problema y valor
   verificable. 5. **Capability** — capacidad abstracta
   tecnológicamente neutra. 6. **Scope** — Factory/fase/tipos de
   tarea/entornos/límites explícitos. 7. **Preconditions** —
   contexto, requisitos, dependencias, autorización, herramientas,
   estado (§13; jamás autorización presunta). 8. **Required Context**
   — mínimo necesario (R-CK-001), identificable y vigente.
9. **Inputs** — requisitos, contexto, artefactos, restricciones,
   estado, evidencia previa, parámetros. 10. **Procedure** —
   reproducible y determinista para su propósito (preparar,
   analizar, ejecutar, controlar, validar, evidenciar, escalar),
   abstracto de herramienta (§14). 11. **Tools** — medios
   sustituibles; `TOOL ≠ SKILL` (§15). 12. **Outputs** —
   consumibles por otra Skill/Agent, validables, trazables;
   output ≠ success (§12). 13. **Validation** — comprobación
   (`EXECUTION ≠ VALIDATION ≠ CERTIFICATION`, §16). 14. **Evidence**
   — archivos/tests/logs/verificaciones/informes (`EVIDENCE ≠
   VALIDATION`, §17). 15. **Failure Conditions** — contexto
   insuficiente, precondición incumplida, herramienta ausente,
   resultado inválido, conflicto, incertidumbre crítica, fallo de
   validación; ante crítica: STOP→PRESERVE→ESCALATE→WAIT (§18).
16. **Escalation** — faltantes, arquitectura, destructivas,
   producción, incertidumbre, fallo crítico, falta de autorización,
   conflictos; sin auto-autoridad (§19). 17. **Related Rules** —
   Rules F1 aplicables citadas, no copiadas (`RULES = ALLOWED`,
   `SKILLS = HOW`, §20). 18. **Changelog** — historial versionado.

## 5. Cadena, lifecycle, versionado, composición (§§11,21–23)

`CAPABILITY → SCOPE → PRECONDITIONS → INPUTS → PROCEDURE →
OUTPUTS → VALIDATION → EVIDENCE` (describe ejecución; no sustituye
Rules/autorización/agente/runtime/gobierno). Lifecycle:
propuesta→definición→revisión→validación→aprobación→activa→
evolución→superseded/deprecated (gobierno F1/F0-S7, sin sistema
nuevo). Composición por principio (Analysis→…→Code Review) sin
implementar Skills. Caso Database Engineering (§24): modelado …
documentación como prueba conceptual de generalidad, sin
desarrollar la Skill.

## 6. Criterios de validación (§27)

Aceptación 1–27 verificada en `F2-S1-VALIDATION.md` (definición,
responsabilidad, alcance, límites, 18 campos, inputs/outputs/
preconditions/procedure/tools/validation/evidence/failure/
escalation/related-rules, lifecycle, versionado, composición,
independencias agent/runtime/tecnología/OpenCode, caso DB,
coherencia F1/F0, sin F2-S2, evidencia para revisión).
