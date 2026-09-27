# TOOLING-BASELINE — AI Software Factory — F0-S6 Herramientas y entorno

Fase: F0 — Fundaciones.
Sprint: F0-S6 — Herramientas y entorno.
Estado: definición documental y estratégica. No implementa tooling.

Este documento fija el entorno base mínimo con el que la Factory puede
empezar a materializarse profesionalmente sin comprometer su evolución.
Responde a la pregunta: ¿cuál es el mínimo toolset necesario para operar
profesionalmente y permitir evolución futura? No a: ¿qué herramientas
podríamos añadir?

Principio rector: el tooling sirve a la arquitectura (F0-S4); el tooling
no define arbitrariamente la arquitectura (P21).

## 1. Objetivo

Disponer de un entorno base verificable, reproducible en evolución y
gobernado, que soporte el lifecycle F0-S5 sobre los componentes F0-S4,
manteniendo cada herramienta reemplazable y cada capacidad futura
claramente marcada como no implementada.

## 2. Entorno base

```text
Machine (local del desarrollador)
+
Repository (Git + GitHub)
+
OpenCode (entorno de trabajo asistido)
+
Documentación versionable (Markdown + Mermaid)
=
Entorno base ACTUAL
```

Estrategia local-first (P22): la Factory prioriza lo local mientras sea
suficiente para validar capacidades. La complejidad remota (ejecución
prolongada, supervisión, disponibilidad, notificaciones, operación
distribuida) se incorporará solo ante necesidad real justificada. Fases
de evolución previstas: A local → B validación automatizada → C
capacidades IA controladas → D orquestación → E supervisión remota (ver
`TOOL-SELECTION.md` y `toolchain.mmd`).

## 3. Herramientas actuales verificables

Leyenda de estado: `ACTUAL` = verificada en este repositorio/entorno;
`NO VERIFICADO` = no puede comprobarse en F0-S6; `FUTURO` = diferido.

| Herramienta | Estado | Propósito | Responsabilidad (F0-S4) |
|-------------|--------|-----------|-------------------------|
| Git | ACTUAL | Control de versiones, registro de evidencia y recuperación | Soporta Traceability (C12), Recovery (C13), Evolution versionada (C15, P19) |
| GitHub (repositorio, branches, PRs, merges) | ACTUAL | Colaboración, revisión, integración y traza remota | Soporta Validation (C10), Evidence (C11), Human Gates de integración |
| OpenCode | ACTUAL | Entorno de trabajo asistido por IA donde el humano dirige Tasks | Posición detallada en `OPENCODE.md`; no es la arquitectura |
| Markdown | ACTUAL | Documentación versionable legible | Soporta Knowledge (C06, P18) |
| Mermaid | ACTUAL | Diagramas versionables y revisables por Git | Soporta documentación arquitectónica sin infraestructura adicional |
| Terminal y editor locales | ACTUAL | Operación del entorno por el desarrollador | Genéricos y reemplazables; sin marca obligatoria |

Explícitamente fuera de la baseline actual (FUTURO / NO IMPLEMENTADO):
Agents funcionales, Skills funcionales, Rules operativas formalizadas —
FUTURO / F1, Orchestrator
funcional, GitHub Actions, CI/CD, observabilidad, recovery automation,
remote supervision, autonomía condicionada. Distinción: Rules
conceptuales (Task → Rules → Orchestrator, F0-S4; principios F0-S3) =
ACTUAL; Rules operativas formalizadas = FUTURO. No se declara que Rules
conceptualmente sean futuras.

## 4. Clasificación

```text
CORE — imprescindible para operar hoy (Git, GitHub, OpenCode, Markdown, Mermaid)
PROJECT — específico de este repositorio (estructura docs/, .gitignore, LICENSE, README)
OPTIONAL — a elección del desarrollador sin afectar la traza (editor, terminal concreto)
FUTURE — requerido solo cuando la evidencia lo justifique (Actions, CI/CD, observabilidad, orquestación, supervisión remota)
```

Nada se agrega para completar listas: cada entrada CORE responde a una
necesidad demostrada del lifecycle actual (definir, versionar, revisar,
trazar).

## 5. Dependencia y límites

- La Factory depende conceptualmente de responsabilidades (versionar,
  revisar, trazar, validar), no de marcas: cada CORE es sustituible si
  otra herramienta cubre la misma responsabilidad con igual o mejor
  evidencia (ver reemplazabilidad en `TOOL-SELECTION.md`).
- Límites: ninguna herramienta de la baseline autoriza por sí misma
  (capability ≠ authority); ninguna ejecuta fuera de decisión humana;
  ninguna contiene la lógica del lifecycle (el lifecycle vive en los
  documentos, no en las herramientas).
- Least Privilege (P09), sin implementar permisos reales en esta fase:

```text
Agent
→ Required Skill
→ Required Tool
→ Minimum Permission
```

Nunca `Agent → Full System Access`. Conceptualmente: mínimo
privilegio, permisos explícitos, acceso limitado, capacidad
controlable, herramientas observables, acciones validables y
posibilidad de limitar o retirar acceso.
- `Configuration ≠ Secrets`: ningún secreto vive en Git, en
  documentación, en prompts, en logs ni en evidencias sin protección. La
  gestión detallada de secretos queda diferida a fases posteriores.

## 6. Relación con la Factory

Cada herramienta CORE mapea a responsabilidades F0-S4 sin reasignarlas:

```text
Human / Task / Rules → se expresan en Git + GitHub + documentos
Orchestrator / Agents / Skills → FUTURO (posición reservada, sin implementación)
Context / Knowledge → Markdown + Mermaid versionados
Tools → capacidades técnicas utilizadas dentro del entorno (OpenCode
media Tools; utilidades locales genéricas). Rige `OpenCode ≠ Tools`:
OpenCode es el entorno actual de trabajo asistido; Tools son las
capacidades técnicas utilizadas dentro del entorno. OpenCode puede
utilizar o mediar Tools, pero no equivale a la categoría arquitectónica
Tools (C08).
Execution / Validation / Evidence / Traceability → Git + GitHub + revisión humana
Recovery → Git como soporte de registro, reversión y recuperación de
cambios (manual en esta fase). Recovery continúa siendo una
responsabilidad del workflow (F0-S5) y actualmente se realiza de forma
manual. Rige `Recovery ≠ Tool` y `Git ≠ Recovery`: Git proporciona
mecanismos útiles (historial, comparación, reversión, recuperación de
cambios, evidencia) pero no sustituye el proceso de Recovery.
Measurement / Evolution → FUTURO (concebidas, no implementadas)
```

## 7. Evolución prevista

La baseline crece solo con madurez y evidencia:

```text
Phase A — Local Foundation (ACTUAL: Local + Git + GitHub + OpenCode + supervisión manual)
→ Phase B — Validation Automation (FUTURO: scripts + tests + Actions + validación automatizada)
→ Phase C — Controlled AI Capabilities (FUTURO: Agents + Skills + automatización controlada)
→ Phase D — Orchestration (FUTURO: orquestación + observabilidad + recovery)
→ Phase E — Remote Supervision (FUTURO: supervisión remota + autonomía condicionada)
```

Ninguna fase futura se presenta como implementación actual. La
complejidad crece proporcionalmente a madurez y evidencia disponible.

## 8. Separación de entornos

```text
Factory Development
≠
Factory Execution
≠
Product Production
```

- Development Environment (ACTUAL): diseño, programación,
  documentación, pruebas y revisión en local + Git + GitHub + OpenCode.
- Execution Environment (FUTURO): Agents, workflows, Tasks y
  automatización bajo ejecución controlada. Posición reservada, sin
  implementación.
- Production Environment (FUTURO): productos reales, fuera de la
  Factory. El stack de un Product nunca se convierte en stack
  obligatorio de la Factory (Factory ≠ Product).

La Factory no asume que los entornos sean equivalentes: cada uno tiene
responsabilidades, permisos y riesgos distintos.
