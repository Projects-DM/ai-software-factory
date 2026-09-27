# TRACEABILITY — AI Software Factory — F0-S5 Trazabilidad extremo a extremo

Fase: F0 — Fundaciones.
Sprint: F0-S5 — Flujo de trabajo.
Estado: diseño conceptual-operativo. No implementa la Factory.

Este documento define la trazabilidad que atraviesa el lifecycle:
qué se vincula con qué, qué significa cada vínculo y por qué es
necesario. Desarrolla el componente C12 de F0-S4 como parte estructural
del flujo, no como agregado final.

## 1. Cadena de trazabilidad

Cadena conceptual de referencia (los elementos inexistentes para una
Task no se inventan; ver sección 4):

```text
Task ID
↓
Plan
↓
Agent (cuando la ejecución delega en un agente)
↓
Skill (cuando se usa un procedimiento reutilizable)
↓
Execution
↓
Tool Actions (cuando intervienen herramientas)
↓
Changes
↓
Tests
↓
Review
↓
Evidence
↓
Commit / PR
↓
Merge
↓
Deployment (cuando la Task incluye despliegue)
↓
Final Result
```

En forma compacta, la trazabilidad conserva:

```text
Task
→ Plan
→ participantes/capacidades utilizadas
→ ejecución
→ cambios
→ validación
→ evidencia
→ decisión
→ integración
→ despliegue
→ resultado final
```

## 2. Qué significa cada relación y por qué es necesaria

| Vínculo | Significado | Por qué es necesaria |
|---------|-------------|----------------------|
| Task ID → Plan | Todo trabajo deriva de una Task identificada con plan y criterios | Sin origen no hay legitimidad ni alcance: nada se ejecuta "porque sí" |
| Plan → Agent | Cuando la ejecución delega en un agente, cada asignación vincula plan con ejecutor acotado | Permite saber quién actuó, con qué autoridad y bajo qué límites |
| Agent → Skill | Cuando se usa un procedimiento reutilizable, cada ejecución lo invoca de forma identificada | Distingue lo improvisado de lo validado; sostiene P07/P08 |
| Skill → Execution | El procedimiento se materializa en una ejecución acotada observable | Vincula lo prescrito con lo realmente ocurrido |
| Execution → Tool Actions | Cuando intervienen herramientas, cada acción técnica queda registrada contra su ejecución | Permite reconstruir operaciones exactas ante un fallo (diagnóstico) |
| Tool Actions → Changes | Cada cambio (diff, artefacto, configuración) remite a las acciones que lo produjeron | Impide cambios huérfanos sin causa conocida |
| Changes → Tests | Cada cambio se somete a pruebas vinculadas | Sin este vínculo, IMPLEMENTED se confunde con VALIDATED |
| Tests → Review | Los veredictos de pruebas alimentan la revisión | La revisión juzga con evidencia, no a ciegas |
| Review → Evidence | Decisiones y hallazgos de revisión quedan registrados | La aprobación es prueba, no gesto informal |
| Evidence → Commit / PR | La evidencia acompaña al cambio hacia integración | Git/GitHub recibe el cambio con su justificación, no solo su diff |
| Commit / PR → Merge | El merge remite al PR, su CI y su aprobación | Ningún merge sin cadena completa de validación |
| Merge → Deployment | Cuando la Task incluye despliegue, este remite al merge verificado que contiene | Impide desplegar lo no integrado ni validado |
| Deployment → Final Result | El resultado final (COMPLETED) cierra la traza contra la Task original | Permite afirmar finalización con prueba, no por declaración |

## 3. Qué permite la trazabilidad

- Conectar causa y resultado: del objetivo al resultado final sin saltos.
- Reconstruir qué ocurrió: secuencia completa ante auditoría, fallo o
  disputa.
- Identificar qué agente o capacidad produjo cada acción (atribución con
  autoridad, no vigilancia indiscriminada).
- Relacionar cada cambio con la tarea original que lo motivó.
- Conectar validación con evidencia: cada veredicto remite a su prueba.
- Conectar Git/GitHub con el lifecycle: commits, PRs, merges y
  despliegues son nodos de la traza, no historia paralela.
- Permitir análisis y mejora posterior: Measurement (C14) y Evolution
  (C15) solo operan sobre lo trazado (P25, P26, P30).

## 4. Qué no es trazabilidad

> Registrar absolutamente todo sin criterio no es trazabilidad: es ruido.

La trazabilidad debe representar los elementos realmente participantes:
una Task documental puede no tener Agent, Skill, Tool ni Deployment, y
eso no es una carencia sino proporcionalidad. Los elementos inexistentes
para una Task no deben inventarse.

La trazabilidad debe ser suficiente para reconstruir qué ocurrió, por
qué ocurrió, qué se modificó, cómo se validó y qué decisión permitió
avanzar. No registrar por registrar.

La trazabilidad es suficiente y útil cuando cada vínculo responde a una
pregunta de control, diagnóstico o mejora. Se registra lo relevante para
decidir, diagnosticar, auditar y evolucionar; el resto se descarta por
diseño (P12 contexto mínimo, P24 minimización de datos). El criterio es:
si ningún principio, puerta o análisis futuro puede necesitar un dato,
conservarlo es costo sin valor.
