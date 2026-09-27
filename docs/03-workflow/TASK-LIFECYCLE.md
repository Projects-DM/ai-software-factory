# TASK-LIFECYCLE — AI Software Factory — F0-S5 Unidad de trabajo

Fase: F0 — Fundaciones.
Sprint: F0-S5 — Flujo de trabajo.
Estado: diseño conceptual-operativo. No implementa la Factory.

Este documento define el lifecycle de una unidad individual de trabajo
(Task, componente C02 de F0-S4) dentro del lifecycle general descrito en
`DEVELOPMENT-LIFECYCLE.md`. La Task atraviesa los estados canónicos
(DRAFT → PLANNED → READY → IMPLEMENTING → IMPLEMENTED → TESTING →
REVIEW → CERTIFIED → PR → MERGED → DEPLOYED → COMPLETED) definidos allí.
Responde qué es una Task, qué necesita para avanzar y cómo se decide su
siguiente estado.

## 1. Qué es una Task

Una Task es la unidad mínima de trabajo representable, priorizable,
ejecutable, validable y trazable de la Factory. Porta objetivo, alcance,
criterios de aceptación, prioridad y estado. Todo lo que deriva de ella
(plan, asignaciones, cambios, pruebas, revisiones, commits, PRs,
despliegues) se vincula a su identificador. Las necesidades de un Product
nunca redefinen qué es una Task (P29, riesgo R08): la Task describe
trabajo de construcción, no funcionalidad de producto.

## 2. Entradas

Toda Task nace de una entrada explícita:

- solicitante (Human u origen autorizado con trazabilidad al humano);
- objetivo enunciado y alcance propuesto;
- prioridad y contexto inicial disponible.

Sin solicitante identificable ni objetivo enunciado no hay Task: hay
ruido que debe clarificarse antes (P06).

## 3. Precondiciones

Antes de que una Task quede READY debe cumplirse:

- plan existente con pasos comprensibles;
- criterios de aceptación explícitos y comprobables;
- Rules aplicables identificadas (permisos, autonomía delegada,
  validación exigida);
- dependencias y riesgos conocidos o declarados como desconocidos con
  estrategia (puerta humana si procede);
- contexto mínimo necesario localizable (C06).

Si falta información significativa, la Task no avanza por suposición: se
identifica la ambigüedad, se evalúa su impacto, se solicita aclaración y
se documenta la decisión (P06).

## 4. Planificación

La planificación convierte la solicitud en trabajo ejecutable: descompone
el objetivo en pasos, asigna responsabilidades conceptuales (qué rol
ejecutor, qué validación, qué puertas), estima riesgos y fija los
criterios que decidirán el avance. El plan queda documentado y vinculado
a la Task; planificar no es ejecutar y PLANNED no es READY.

## 5. Ejecución

La ejecución (actividad EXECUTE) ocurre en el estado IMPLEMENTING bajo
las Rules: el Orchestrator (C04)
asigna a Agents (C05) con contexto mínimo necesario (C06), que operan vía
Skills (C07) y Tools (C08) dentro de un Execution acotado (C09). Ejecutar
produce resultados observables y registros, nunca declaraciones de éxito.

## 6. Resultado

El resultado es qué produjo la ejecución: cambios, artefactos, registros.
Existe con independencia de su corrección: un resultado puede ser
completo, parcial, inválido o fallido. Registrar el resultado no es
validarlo.

## 7. Validación

La validación contrasta el resultado contra los criterios de aceptación
(TESTING y REVIEW, componente C10, ejercidos por responsabilidades
distintas de quien implementó — P10). Toda validación debe producir una
decisión verificable, cuyo resultado según el contexto conduce a una de
estas vías:

```text
ADVANCE
CHANGES_REQUESTED
RECOVERY
ESCALATION / WAITING_HUMAN
```

Lo ambiguo escala a humano; lo rechazado con observaciones corregibles
vuelve a IMPLEMENTING como CHANGES_REQUESTED; la condición realmente
fallida entra en Recovery.

## 8. Evidencia

La evidencia demuestra lo ocurrido: diffs, test reports, revisiones
registradas, logs, resultados de CI, decisiones de avance. Cada pieza se
vincula al identificador de la Task. Sin evidencia vinculada no hay
avance legítimo, por mucho que el estado lo sugiera.

## 9. Decisión

La decisión determina qué hacer después a partir de validación y
evidencia: avanzar, devolver con cambios, bloquear, escalar a humano,
recuperar, cancelar. La decide quien tenga autoridad para ese tipo de
transición (humano, rol designado u Orchestrator dentro de Rules);
capability ≠ authority.

## 10. Transición

La transición mueve la Task al siguiente estado siguiendo el esquema
Current State → Condition → Validation → Evidence → Authorized Decision
→ Next State (`DEVELOPMENT-LIFECYCLE.md`, sección 5) y queda registrada
con su justificación. Ninguna transición es automática por defecto.

## 11. Separación conceptual STATE / RESULT / VALIDATION / EVIDENCE / DECISION

```text
STATE
→ dónde está la tarea

RESULT
→ qué produjo la ejecución

VALIDATION
→ si el resultado cumple

EVIDENCE
→ cómo se demuestra

DECISION
→ qué hacer después
```

Ejemplo conceptual:

```text
State:
IMPLEMENTED

Result:
Cambio producido.

Validation:
Tests PASS.

Evidence:
Diff + test report.

Decision:
Move to REVIEW.
```

Cada plano responde una pregunta distinta y ninguno sustituye a otro:
el estado sitúa, el resultado informa, la validación juzga, la evidencia
prueba y la decisión mueve. En términos operativos:

```text
Test ejecutado
→ Validation (comprobación de criterios)

Resultado del test / reporte
→ Evidence (información que demuestra qué ocurrió)

Autorizar avance
→ Decision (determinación autorizada sobre qué hacer después)
```

No tratar evidencia como validación. No tratar ejecución como éxito.

> El estado nunca debe utilizarse como sustituto de validación o evidencia.

Estar en REVIEW no significa estar revisado; estar en TESTING no
significa tener pruebas superadas; estar en CERTIFIED sin evidencia
vinculada es una contradicción que debe reportarse, no un avance
(riesgo R03: IMPLEMENTED ≠ CERTIFIED). En forma compacta:

```text
IMPLEMENTED
≠
VALIDATED
```

```text
TESTING ≠ tests aprobados
REVIEW ≠ review aprobada
CERTIFIED sin evidencia suficiente = contradicción
```
