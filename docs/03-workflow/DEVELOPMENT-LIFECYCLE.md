# DEVELOPMENT-LIFECYCLE — AI Software Factory — F0-S5 Flujo de trabajo

Fase: F0 — Fundaciones.
Sprint: F0-S5 — Flujo de trabajo.
Estado: diseño conceptual-operativo. No implementa la Factory.

Este documento define el lifecycle general de desarrollo: cómo se mueve
una unidad de trabajo desde su entrada hasta su finalización, incluyendo
bloqueos, fallos, recuperación, cancelación e intervención humana. Es
documentación versionable, no una máquina de estados en código, ni
infraestructura, ni automatización.

Documentos relacionados: `TASK-LIFECYCLE.md` (unidad individual),
`HUMAN-GATES.md` (puertas humanas), `TRACEABILITY.md` (traza extremo a
extremo), `task-lifecycle.mmd` (diagrama).
Base: `docs/01-foundations/` (F0-S1–S3), `docs/02-architecture/` (F0-S4).

## 1. Propósito

El lifecycle existe para que el trabajo de ingeniería sea representable,
predecible y auditable: en todo momento debe poder responderse dónde está
una tarea, qué falta para que avance, quién puede autorizar el avance y
qué evidencia lo respalda. Sin lifecycle explícito, cada ejecución
improvisa su propio camino y la trazabilidad, la recuperación y la
medición carecen de puntos de anclaje. El problema que resuelve es el de
F0-S1: sustituir la coordinación manual e inconexa por un proceso
estructurado donde ejecutar, validar, evidenciar y trazar ocurren en
orden y con responsables definidos (componentes C01–C15 de F0-S4).

## 2. Lifecycle principal

Estos son los estados canónicos del lifecycle de una Task. Camino
nominal de una unidad de trabajo:

```text
DRAFT
↓
PLANNED
↓
READY
↓
IMPLEMENTING
↓
IMPLEMENTED
↓
TESTING
↓
REVIEW
↓
CERTIFIED
↓
PR
↓
MERGED
↓
DEPLOYED
↓
COMPLETED
```

No se introducen sinónimos alternativos como estados equivalentes. Las
actividades conceptuales (REQUEST, PLAN, EXECUTE, TEST, REVIEW,
INTEGRATE, DEPLOY, VALIDATE, RECOVER) describen qué se hace, no dónde
está la Task: `EXECUTE` no es un estado, `INTEGRATE` no es un estado y
`DEPLOY` no es un estado. El estado refleja la condición observable de
la Task. El diagrama `task-lifecycle.mmd` representa este mismo modelo
canónico.

Deliberadamente doce estados principales: suficientes para distinguir
planificar de ejecutar, ejecutar de validar y validar de integrar
(incluyendo PR, merge y despliegue como condiciones observables
diferenciadas); sin decenas de micro-estados que solo añadirían ruido
(riesgo R01, R10).

## 3. Estados

| Estado | Significado | Condición de entrada | Condición de salida | Evidencia esperada | Responsable conceptual |
|--------|-------------|----------------------|---------------------|--------------------|------------------------|
| DRAFT | Solicitud o trabajo inicialmente enunciado; aún no implica planificación completa ni autorización para ejecución | Necesidad expresada por el Human (C01) | Objetivo y alcance enunciados | Registro de la solicitud vinculada al solicitante | Human |
| PLANNED | La solicitud fue convertida en trabajo planificado, con suficiente definición para determinar alcance, criterios, dependencias, riesgos y forma de validación | DRAFT aceptada a trámite | Plan + criterios de aceptación definidos | Plan documentado y criterios explícitos | Human con asistencia |
| READY | La Task cumple las precondiciones necesarias para comenzar: objetivo, alcance, criterios de aceptación, Rules aplicables, dependencias, riesgos conocidos y contexto mínimo necesario | Plan aprobado, Rules aplicables identificadas, precondiciones cumplidas | Asignación autorizada | Aprobación registrada, precondiciones verificadas | Orchestrator / rol autorizado según Rules |
| IMPLEMENTING | La Task se encuentra en ejecución, acotada por responsabilidades, permisos, Rules y contexto | Recursos, permisos y contexto mínimo disponibles | Resultado producido y observable | Registros de operación | Agents |
| IMPLEMENTED | Existe un resultado/cambio producido. `IMPLEMENTED ≠ VALIDATED`: no significa que el resultado sea correcto | Resultado observable entregado | Resultado sometido a validación | Diff / artefactos del cambio | Agents |
| TESTING | El resultado está siendo contrastado contra criterios definidos | Cambio sometido a pruebas | Veredicto de pruebas emitido | Test reports | Testing (responsabilidad separada del implementador, P10) |
| REVIEW | El resultado está siendo sometido a revisión; estar en este estado no implica aprobación | Tests superados | Aprobación o solicitud de cambios | Revisión registrada con decisión | Reviewer |
| CERTIFIED | Los criterios aplicables fueron satisfechos y existe evidencia suficiente para autorizar la integración | Review aprobada | Autorización de integración | Certificación vinculada a evidencia previa | Human / rol designado |
| PR | Existe una propuesta formal de integración mediante Pull Request. Se distingue entre existencia del PR, checks, revisión, aprobación y merge: abrir un PR no implica integración | Certificación vigente | PR aprobado con checks superados | PR + revisiones + resultados de CI | Orchestrator / Integración |
| MERGED | El cambio fue integrado en la rama correspondiente y la integración fue verificada según los criterios aplicables | PR aprobado | Merge verificado con CI en verde | Merge + resultados de CI | Orchestrator / Integración |
| DEPLOYED | El cambio fue desplegado y el despliegue fue verificado según el alcance definido | Merge verificado | Despliegue verificado | Registro de release/deploy y verificación | Operación designada |
| COMPLETED | El resultado final está aceptado y la trazabilidad requerida está cerrada | Despliegue verificado (cuando la Task incluye despliegue) y traza cerrada | — (estado final) | Traza extremo a extremo cerrada | Human (cierre) |

## 4. Estados excepcionales

```text
BLOCKED
FAILED
RECOVERING
WAITING_HUMAN
CHANGES_REQUESTED
CANCELLED
CLOSED
```

| Estado | Significado | Se entra desde |
|--------|-------------|----------------|
| BLOCKED | Existe una condición externa o dependencia que impide continuar (falta información, dependencia, riesgo). Puede ocurrir desde cualquier estado operativo en el que una condición externa impida continuar. No significa que el trabajo haya fallado | Según el estado afectado |
| FAILED | Una operación o resultado no cumplió la condición esperada; requiere clasificación y diagnóstico. No implica automáticamente que toda la Task quede cancelada | IMPLEMENTING, IMPLEMENTED, TESTING, PR, MERGED, DEPLOYED |
| RECOVERING | Fase excepcional de diagnóstico y recuperación (P14, P15). `RECOVERING ≠ RETRY`: una repetición solo procede después de determinar que es segura y apropiada; sin retry automático ni infinito | FAILED, BLOCKED |
| WAITING_HUMAN | Espera por decisión o autorización humana en un Human Gate. No es simplemente un error | Cualquier estado con puerta o escalado |
| CHANGES_REQUESTED | Devolución con observaciones que requieren trabajo adicional; regresa a `CHANGES_REQUESTED → IMPLEMENTING` (no existe `EXECUTE` como estado de retorno) | REVIEW → IMPLEMENTING |
| CANCELLED | Decisión explícita de no continuar; la tarea se archiva con su evidencia | Cualquier estado autorizado previo a COMPLETED |
| CLOSED | Archivo administrativo de una tarea CANCELLED o COMPLETED | CANCELLED, COMPLETED |

Distinciones obligatorias:

```text
BLOCKED ≠ FAILED
```

Bloqueo es espera por causa externa con ejecución intacta; fallo es
resultado inválido o terminación incorrecta. Confundirlos lleva a
reintentar lo que hay que desbloquear, o a diagnosticar lo que solo
requiere esperar.

```text
FAILED ≠ RECOVERING
```

Fallo es el hecho; recuperación es el proceso diagnosticado que le sigue.
Entrar en RECOVERING exige clasificar y preservar evidencia, no solo
constatar el fallo.

```text
RECOVERING ≠ RETRY
```

Recuperación es comprender–diagnosticar–recuperar–validar; reintento es
repetir la operación. Todo reintento sin diagnóstico es repetición ciega
y está prohibido (P15, riesgo R05).

```text
CANCELLED ≠ FAILED
```

```text
WAITING_HUMAN ≠ FAILED
WAITING_HUMAN ≠ BLOCKED
```

Cancelar es una decisión explícita y trazada de no continuar; fallar es
un resultado involuntario. Una tarea cancelada no es una tarea fallida y
su evidencia se preserva igualmente. Esperar una decisión humana no es
fallar ni estar bloqueado: WAITING_HUMAN preserva estado y evidencia a
la espera de autorización.

## 5. Transiciones

Toda transición entre estados sigue este esquema; ninguna es automática
por defecto (riesgo R02):

```text
Current State
↓
Condition
↓
Validation
↓
Evidence
↓
Authorized Decision
↓
Next State
```

- Condition: qué debe ser cierto para poder avanzar (incluye
  precondiciones y puertas superadas).
- Validation: contraste contra criterios antes del avance (P03).
- Evidence: prueba registrada del cumplimiento (un estado nunca es
  evidencia de sí mismo, ver sección 10).
- Authorized Decision: quién autoriza (humano, rol designado u
  Orchestrator dentro de Rules) según riesgo y autoridad
  (capability ≠ authority).

## 6. Flujo normal (camino feliz)

```text
DRAFT → PLANNED → READY → IMPLEMENTING → IMPLEMENTED → TESTING →
REVIEW → CERTIFIED → PR → MERGED → DEPLOYED → COMPLETED
```

1. El Human enuncia la necesidad (actividad REQUEST, estado DRAFT) y la
   convierte en Task con plan y criterios (actividad PLAN, estado
   PLANNED).
2. Verificadas precondiciones y Rules, la Task queda READY y se asigna.
3. Los Agents ejecutan (actividad EXECUTE, estado IMPLEMENTING) y
   producen el cambio (IMPLEMENTED).
4. Testing emite veredicto; Review aprueba; la Task queda CERTIFIED.
5. Se propone la integración (PR), se verifica el merge (MERGED), se
   verifica el despliegue (DEPLOYED) y se cierra (COMPLETED) con la
   traza completa vinculada a la Task original.

## 7. Excepciones

- Validación que falla: no se avanza. La respuesta depende de la
  naturaleza del hallazgo (no toda revisión negativa es FAILED ni todo
  hallazgo exige CHANGES_REQUESTED):
  ```text
  REVIEW
   ├─ observaciones corregibles → CHANGES_REQUESTED → IMPLEMENTING
   └─ condición realmente fallida → FAILED → RECOVERING / escalamiento
  ```
  En TESTING en contra, el resultado se clasifica como FAILED y entra
  en Recovery; el camino feliz se retoma solo tras nueva validación.
- Bloqueo (dependencia externa, falta de información): la tarea pasa a
  BLOCKED con causa registrada; de allí a WAITING_HUMAN si requiere
  decisión. Volver a READY no es automático: exige resolver la
  condición bloqueante y validar nuevamente las precondiciones antes de
  continuar desde el estado apropiado.
- Falta de información o ambigüedad significativa: se aplica P06 (no
  inventar requisitos): identificar, evaluar impacto, solicitar
  aclaración, documentar la decisión; la tarea espera en WAITING_HUMAN,
  nunca avanza por suposición.
- Riesgo detectado (acción irreversible, cambio sensible, incertidumbre):
  se activa el Human Gate correspondiente; sin autorización no hay
  avance.
- Intervención humana requerida: WAITING_HUMAN preserva estado y
  evidencia; la reanudación exige decisión registrada.
- Revisión que solicita cambios: REVIEW → CHANGES_REQUESTED →
  IMPLEMENTING, conservando observaciones y versiones anteriores.
- Ejecución que falla: IMPLEMENTING → FAILED con evidencia preservada;
  entra Recovery (sección 8), nunca reintento directo.

## 8. Recovery

Modelo conceptual de recuperación (P14, P15; componente C13). No toda
recuperación sigue obligatoriamente el mismo camino: el retorno depende
del contexto.

```text
Failure / Block
→ Classify
→ Preserve Evidence
→ Diagnose
→ Recover
→ Validate
→ Continue / Escalate
```

- Classify: distinguir fallo de bloqueo, y fallo recuperable de fallo
  que exige escalado (BLOCKED ≠ FAILED).
- Preserve Evidence: congelar registros, diffs, logs y estado antes de
  cualquier intento correctivo.
- Diagnose: determinar causa probable con la evidencia preservada.
- Recover: aplicar la corrección acotada (reversibilidad preferente,
  P17; idempotencia cuando sea viable, P16).
- Validate: comprobar que la recuperación es efectiva contra criterios.
- Continue / Escalate: la Task regresa al estado operativo apropiado,
  determinado por el punto del lifecycle afectado y por la validación
  posterior (sin destino universal obligatorio: ni siempre a
  IMPLEMENTING ni siempre a TESTING), o escala al humano si no hay vía
  segura.

Principio rector:

**Retry ≠ Recovery**

No existe ningún modelo de reintento infinito: cada reintento cuenta,
exige diagnóstico previo y tiene un límite; agotado el límite o ante
riesgo, la única vía es escalar (riesgo R05).

## 9. Cancelación

```text
CANCELLED
↓
CLOSED
```

- CANCELLED requiere decisión explícita autorizada (humano o rol con
  autoridad delegada para ello), con motivo registrado, desde cualquier
  estado autorizado previo a COMPLETED.
- La evidencia generada hasta el momento se preserva y se vincula a la
  Task; cancelar no borra historia (CANCELLED ≠ FAILED).
- CLOSED es cierre administrativo/archivo, no un estado operativo
  principal del lifecycle: puede utilizarse después de `COMPLETED →
  CLOSED` o `CANCELLED → CLOSED` si se considera necesario ese cierre
  administrativo. Ninguna tarea cancelada puede reactivarse como si
  nada: reabrir exige nueva decisión trazada.

## 10. Validation / Evidence

```text
IMPLEMENTED ≠ VALIDATED
```

Producir un cambio no demuestra que el cambio sea correcto. Por eso:

- IMPLEMENTED solo afirma "el cambio existe"; TESTING y REVIEW afirman
  "el cambio cumple", y CERTIFIED lo declara integrable;
- un estado no constituye evidencia por sí mismo: estar en TESTING no
  prueba que las pruebas pasaron; lo prueba el test report vinculado;
- cada avance de estado exige evidencia externa al estado (artefacto,
  registro, veredicto) conforme al esquema de transiciones (sección 5);
- el principio de avance es DO → CHECK → PROVE → DECIDE → ADVANCE,
  nunca DO → ASSUME → ADVANCE (ver sección 11).

## 11. Principio de avance y su anclaje en F0-S3

```text
DO
↓
CHECK
↓
PROVE
↓
DECIDE
↓
ADVANCE
```

Nunca:

```text
DO
↓
ASSUME
↓
ADVANCE
```

Correspondencia con principios de F0-S3:

- P03 (evidencia antes de avanzar): CHECK y PROVE son obligatorios.
- P05 (no romper lo existente): CHECK incluye impacto sobre
  funcionalidad, pruebas, documentación y despliegue.
- P13 (trazabilidad extremo a extremo): PROVE genera registros
  vinculados a la Task.
- P14 (fallar de forma segura): ante CHECK negativo, detener y
  preservar antes que avanzar.
- P15 (recuperar antes de repetir): DECIDE exige diagnóstico previo a
  cualquier repetición.
- P25 (medir antes de afirmar mejora): ADVANCE hacia DEPLOYED/COMPLETED
  nunca afirma mejora por velocidad aparente.
- P26 (autonomía ganada con evidencia): DECIDE solo puede delegarse en
  la medida validada para ese tipo de tarea.

## 12. Idempotencia

Conceptualmente (P16; sin implementar mecanismos en este sprint):

```text
Operation
↓
Execute
↓
Same request repeated
↓
No unintended duplicated effect
```

Se aplica como criterio de diseño a cambios, despliegues,
notificaciones, integraciones, automatizaciones y acciones remotas:
repetir una operación segura no debe producir efectos duplicados
inesperados. Donde la idempotencia no sea viable, la excepción se
identifica explícitamente y la operación exige autorización y validación
reforzadas.
