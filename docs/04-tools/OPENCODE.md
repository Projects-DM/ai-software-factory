# OPENCODE — AI Software Factory — F0-S6 Posición de OpenCode

Fase: F0 — Fundaciones.
Sprint: F0-S6 — Herramientas y entorno.
Estado: definición documental y estratégica. No configura ni implementa OpenCode.

OpenCode es el entorno actual de trabajo asistido por IA (F0-S1): el
lugar donde el humano dirige Tasks con asistencia, no la arquitectura de
la Factory. La pregunta que lo gobierna es qué capacidad necesita la
Factory (P21); OpenCode es una respuesta actual y reemplazable, no una
premisa.

## 1. Posición en el flujo

```text
Human
→ Task
→ OpenCode
→ Context / Rules
→ Agent
→ Skill
→ Tools
→ Execution
→ Validation
→ Evidence
```

OpenCode ocupa la franja de asistencia y ejecución supervisada: provee
contexto, invoca capacidades y registra operación. No decide objetivos,
no autoriza, no valida por sí mismo, no sustituye al Orchestrator futuro
(P11) ni a los Human Gates (F0-S5).

## 2. Función actual (ACTUAL)

- Asistir al humano en análisis, planificación, especificación,
  implementación, testing, revisión y documentación dentro de Tasks
  definidas por el humano.
- Operar bajo supervisión directa (niveles 1–2 del modelo conceptual;
  ningún nivel declarado como capacidad validada).
- Producir resultados observables con registros que alimentan evidencia
  y trazabilidad manual.

## 3. Relaciones

- Agents: OpenCode es el entorno donde hoy actúa la asistencia; los
  Agents futuros (F2/F3) tendrán responsabilidades acotadas propias. Hoy:
  asistencia supervisada, NO Agents funcionales.
- Skills: hoy no existen Skills funcionales; los procedimientos se
  aplican ad hoc bajo criterio humano. Las Skills futuras se evaluarán
  antes de formalizarse (P07).
- Tools: OpenCode media capacidades técnicas sin otorgarles autoridad
  (Tool ≠ Authority).
- Trazabilidad: lo operado en OpenCode se traza cuando queda registrado
  en documentos y Git; lo que solo vive en la sesión no es traza (P18).

## 4. Límites y responsabilidades que NO posee

- No define objetivos, prioridades ni arquitectura.
- No otorga permisos ni amplía autonomía.
- No declara éxito (Execution ≠ Success; IMPLEMENTED ≠ VALIDATED).
- No sustituye revisión, validación ni Human Gates.
- No conserva conocimiento por sí mismo: lo crítico se traslada a
  artefactos versionados (P18, P19).

## 5. Supervisión humana

Toda operación relevante es iniciada o autorizada por el humano, con
capacidad de detener, corregir o descartar. Ante ambigüedad, el sistema
pregunta y espera (P06); ante excepción, escala (P14, P15).

## 6. Evolución y diferidos

OpenCode evolucionará como una herramienta más: utilizable mientras
aporte valor verificable, sustituible cuando otra cubra mejor la
responsabilidad. Quedan diferidos a fases posteriores (especialmente
F2/F3/F7 según corresponda): Agents funcionales, Skills funcionales,
Orchestrator, bucles autónomos y recovery automation. Nada de ello se
presenta como actual.
