# RUNTIME-PORTABILITY-RECOMMENDATIONS — Recomendaciones de portabilidad

Base: `RUNTIME-DECOUPLING-AUDIT.md` (D0 ×5, D1 ×5, D2 ×0, D3 ×0,
riesgos R1–R4). Sin bloqueantes. Nada aquí modifica F0/Rules; son
condiciones y propuestas para F2/F3 y revisiones humanas.

## 1. Cambios obligatorios: ninguno

No existe acoplamiento técnico que extirpar (cero configs, cero
código, cero estado en memoria privada). Exigir cambios ahora violaría
"no desacoplar por desacoplar".

## 2. Condiciones de entrada F2/F3 (recomendadas, vinculantes al diseñar)

- REC-01: F2 definirá formato Factory-native de Skill (contenido
  portable) con `SKILL.md` solo como representación inicial tras
  adapter. Evita R2.
- REC-02: F3 separará Agent Contract (responsabilidad, contexto,
  herramientas, permisos, entradas/salidas, evidencia, escalado) de
  parámetros runtime-specific (modelo, modo, flags OpenCode).
- REC-03: F2/F3 incluirán mapeo Factory Authorization → Runtime
  Permission (allow/ask/deny como implementación, nunca autoridad).
- REC-04: checklist de cierre de sesión (estado, decisiones,
  evidencia, next action registrados fuera de la sesión). Mitiga R1/R3.
- REC-05: prohibido almacenar estado normativo en memoria de sesión
  (extiende P18; `STATE ≠ AGENT MEMORY`).

## 3. Opcionales

- REC-06: espejar `OPENCODE.md` por runtime futuro (D1→D0 documental).
- REC-07: nodo por runtime en `toolchain.mmd` tras definir adapter.
- REC-08: RP-TEST-001 (diseño §5) ejecutable cuando exista estado
  persistido más allá de Git.

## 4. Mecanismos OpenCode aprovechables (sin convertirlos en arquitectura)

Descubrimiento `SKILL.md` (varias rutas), agentes Markdown con
modelo/modo/permisos, permisos allow/ask/deny por agente: usar como
implementación inicial tras la frontera adapter, nunca como norma.

## 5. Factory Contract (mínimo exigible a todo runtime autorizado)

```text
INPUT → Task → Objective → Scope → Applicable Rules →
Necessary Context → Authorized Tools → Execution → Evidence →
Validation → Result → State → Next Action / Escalation
```

Reemplazable quien lo cumpla con evidencia.

## 6. Runtime Adapter (concepto)

Frontera explícita que traduce: Agent Contract ↔ parámetros del
runtime; Factory Authorization ↔ permisos del runtime; Skill
Factory-native ↔ formato del runtime; estado Factory ↔
sesión/artefactos. Sin lógica de Factory dentro del adapter.

## 7. State Portability (campos fuera de cualquier agente)

TASK_ID, OBJECTIVE, SCOPE, CURRENT_STATE, APPLICABLE_RULES,
DECISIONS, ASSUMPTIONS, FILES_CHANGED, ACTIONS_PERFORMED, EVIDENCE,
TEST_RESULTS, VALIDATION, BLOCKERS, RISKS, NEXT_ACTION,
REQUIRED_HUMAN_DECISION. Existen hoy: vía Git+docs+PRs (manual).
A diseñar: formato de handoff y checklist REC-04.

## 8. RP-TEST-001 (diseño conceptual, no ejecutado)

Crear tarea → Runtime A ejecuta parcial → interrumpir → persistir
estado+evidencia → cerrar sesión → Runtime B recupera → continúa →
valida → evidencia → registra. Esperado: `Agent A → Persisted Factory
State → Agent B`, jamás vía memoria privada. Requiere estado
persistido (F2/F3); hoy verificable solo en forma documental/Git.
