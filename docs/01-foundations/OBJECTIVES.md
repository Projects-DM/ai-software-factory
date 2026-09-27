# OBJECTIVES — AI Software Factory — F0-S2 Objetivos

Fase: F0 — Fundaciones.
Sprint: F0-S2 — Objetivos y North Star.
Estado: conceptual y documental. No implementa la Factory.

Este documento establece la dirección estratégica de la Factory: qué quiere
conseguir y cómo se definirá el éxito. Formula dirección del sistema, no
funcionalidades implementadas. Ninguna capacidad descrita aquí debe leerse
como existente o validada.

Documentos relacionados: `PROJECT-SCOPE.md` y `SCOPE-BOUNDARIES.md` (F0-S1),
`NORTH-STAR.md` (F0-S2).

## 1. Propósito de los objetivos

Dar una referencia estable para decidir qué construir, en qué orden, con
qué límites y cómo saber si la Factory evoluciona en la dirección correcta.
Sin objetivos explícitos, cada decisión de diseño o automatización quedaría
a criterio del momento y sin trazabilidad respecto al propósito definido
en F0-S1.

## 2. Relación con F0-S1

F0-S1 respondió: qué somos, qué problema resolvemos, qué está dentro y qué
está fuera. F0-S2 parte de esa base sin contradecirla:

- mantiene la identidad: Factory = sistema / proceso / instrumentación,
  Product = aplicación concreta construida con la Factory;
- mantiene el problema central: coordinación y sistematización del proceso
  de ingeniería, no "escribir código más rápido";
- mantiene los actores y su autoridad diferenciada (el humano como única
  autoridad final);
- mantiene las fronteras: F0-S1 no implementó agentes, Skills, Rules
  operativas, Orchestrator, automatización compleja, infraestructura,
  producción autónoma ni piloto; F0-S2 tampoco los implementa;
- mantiene SGC-DM como referencia externa de aprendizaje, fuera de la
  Factory.

Si se detectara una contradicción con F0-S1, no se corrige silenciosamente:
se clasifica como PASS / WARN / FAIL indicando documento y sección. En esta
revisión: coherencia con F0-S1 = PASS (ver sección 17 y validación de
`NORTH-STAR.md`).

## 3. Objetivo general

Evolucionar desde la coordinación manual entre humano, IA, herramientas,
código, pruebas, documentación y Git hacia un sistema de ingeniería
progresivamente autónomo, verificable y trazable, que reduzca el trabajo
manual del desarrollador sin degradar la calidad y manteniendo control
humano, capacidad de recuperación y mejora continua.

Este objetivo es dirección. No describe una capacidad implementada ni
validada.

## 4. Objetivos estratégicos

Dirección del sistema, formulada como objetivos a alcanzar
progresivamente en F1–F11, no como estado actual:

1. Reducir el trabajo manual de coordinación a lo largo del ciclo de
   ingeniería (análisis → planificación → especificación → implementación
   → testing → revisión → documentación → Git → CI/CD).
2. Hacer verificable cada entrega: criterios de aceptación explícitos y
   evidencia comprobable.
3. Hacer trazable cada decisión y cada cambio: del objetivo al código, a
   la prueba, a la documentación y al registro Git.
4. Condicionar toda automatización y toda autonomía a evidencia,
   validación y límites conocidos, con Human Gates en acciones críticas.
5. Garantizar la recuperación ante errores, excepciones y degradación.
6. Convertir el trabajo en conocimiento reutilizable solo cuando la
   evidencia lo justifique (no automatizar por defecto).
7. Hacer de la Factory un entorno de aprendizaje que mejore al
   desarrollador y al propio sistema de forma continua.

## 5. Productividad

Productividad significa entregar soluciones de calidad con menos trabajo
manual humano, de forma repetible y sostenible. No se reduce a velocidad.

La dirección incluye:

- menos coordinación manual entre herramientas e interacciones con IA;
- menos reconstrucción a posteriori de contexto, evidencia y trazabilidad;
- menos rework evitable mediante especificación, validación y revisión
  estructuradas;
- medición futura sobre trabajo comparable (ver objetivo aspiracional
  20×–30× en `NORTH-STAR.md`).

Una mejora de velocidad acompañada de degradación significativa de calidad
no constituye por sí misma una mejora válida del sistema. Ver `NORTH-STAR.md`,
secciones de calidad y productividad.

## 6. Calidad

La calidad es condición de validez de cualquier mejora de productividad.
Dirección estratégica:

- criterios de aceptación definidos por el humano antes de ejecutar;
- testing y revisión como parte estructurada del proceso, no como
  actividad opcional a posteriori;
- documentación coherente con el código y con las decisiones;
- la calidad futura se evaluará junto a trazabilidad, errores, rework,
  intervención humana y recuperación, nunca como velocidad aislada.

## 7. Trazabilidad

Toda decisión relevante y todo cambio deben poder rastrearse: objetivo →
especificación → implementación → prueba → revisión → documentación →
registro Git. La trazabilidad es la base de la validación, la recuperación,
la medición y la auditoría humana. Sin trazabilidad no hay autonomía
legítima.

## 8. Automatización

La automatización es un medio condicionado, no un fin. Dirección:

- automatizar solo lo validado, con límites explícitos y reversibilidad;
- preferir asistencia y ejecución supervisada antes que ejecución
  autónoma;
- no convertir todo procedimiento en Rule, Skill, Agent, script o
  workflow; la reutilización debe evaluarse antes de formalizarse (ver
  sección 12);
- F0-S2 no define Rules operativas, Agents, Skills, Orchestrator, CI/CD
  ni infraestructura; eso corresponde a F1–F11.

## 9. Autonomía progresiva

La autonomía se gana mediante evidencia, validación y límites conocidos.
Evolución conceptual de referencia (sin declarar ningún nivel como
alcanzado):

```text
Nivel 1 — Asistencia
Nivel 2 — Ejecución supervisada
Nivel 3 — Ejecución autónoma controlada
Nivel 4 — Ejecución autónoma condicionada
```

Reglas de esta dirección:

- autonomía no significa ausencia de control;
- capability ≠ authority: poder ejecutar no autoriza a ejecutar;
- las acciones críticas continúan sujetas a límites y Human Gates;
- el nivel real alcanzado deberá determinarse posteriormente mediante
  evidencia, no por declaración;
- no se promete autonomía total ni producción autónoma.

## 10. Recuperación

El sistema debe poder volver a un estado conocido y válido ante errores,
excepciones o degradación. Dirección: Git como registro de recuperación,
evidencia que permite diagnosticar, límites que contienen el daño y humano
que decide la respuesta. La recuperación es tan estratégica como la
velocidad: un sistema rápido que no se recupera no es válido.

## 11. Conocimiento técnico

El trabajo de ingeniería debe acumularse como conocimiento explícito y
trazable (decisiones, criterios, evidencia, lecciones), no quedar
disperso en conversaciones o memoria individual. Este conocimiento es el
que, solo cuando esté validado, podrá fundamentar futuras Rules, Skills o
automatizaciones en F1–F11.

## 12. Reutilización

Reutilizar significa convertir conocimiento validado en instrumentos
estables del proceso. Dirección:

- la reutilización debe evaluarse antes de convertir procedimientos en
  Rules, Skills, Agents, scripts o workflows;
- criterios de evaluación: frecuencia, estabilidad, evidencia de
  corrección, coste de mantenimiento, riesgo y reversibilidad;
- no todo procedimiento debe automatizarse; automatizar lo inestable o no
  validado multiplica el daño.

## 13. Aprendizaje y desarrollo profesional

La Factory debe funcionar progresivamente como:

- sistema de producción;
- laboratorio de ingeniería;
- entorno de aprendizaje;
- sistema de mejora continua.

El desarrollador (Human / Technical Director) no es un operador a
sustituir, sino el beneficiario del aprendizaje: cada ciclo debe dejarlo
con mejor criterio, mejores especificaciones y mejores decisiones, además
de mejor producto.

## 14. Control humano

El humano conserva, como dirección permanente y no negociable:

- objetivos, prioridades y decisiones arquitectónicas;
- permisos sensibles y criterios de aceptación;
- riesgos, excepciones y decisiones críticas;
- evolución de la propia Factory.

Ningún objetivo de productividad, automatización o autonomía puede
utilizarse para eludir este control. Todo incremento de delegación
requiere aprobación humana explícita.

## 15. Seguridad y límites como dirección estratégica

Los límites son parte de la estrategia, no un obstáculo a ella:

- límites de autonomía (capability ≠ authority, Human Gates);
- límites humanos (sección 14);
- límites tecnológicos (sin stack futuro obligatorio; OpenCode y GitHub
  son entorno actual, evolución futura basada en evidencia, según F0-S1);
- límites temporales (actual / previsto / futuro, sin presentar futuro
  como existente).

La seguridad del proceso —no delegar sin autorización, no operar fuera de
límites, no presentar lo no validado como válido— es objetivo estratégico
en sí misma.

## 16. Criterios generales de éxito

F0-S2 define éxito como dirección verificable en fases posteriores
(principalmente F10/F11), no como métricas definitivas actuales:

- menos trabajo manual humano sobre trabajo comparable, medido como
  hipótesis aspiracional 20×–30× (ver `NORTH-STAR.md`), acompañado por
  indicadores de calidad, trazabilidad, errores, rework, intervención y
  recuperación;
- entregas verificables contra criterios de aceptación humanos;
- trazabilidad completa de decisiones y cambios;
- recuperación demostrada ante fallos;
- conocimiento acumulado y reutilización justificada por evidencia;
- mejora del criterio del desarrollador, no solo del artefacto.

Estado del conocimiento: todo lo anterior es objetivo / hipótesis /
aspiración. Rigen:

```text
IMPLEMENTED ≠ VALIDATED
```

```text
ASPIRATIONAL ≠ ACHIEVED
```

## 17. Relación con F0-S3

F0-S2 responde: qué queremos conseguir, hacia dónde evolucionamos y cómo
definimos éxito. F0-S3 responderá: qué principios guiarán las decisiones
para conseguirlo. F0-S2 es entrada obligatoria de F0-S3: ningún principio
de F0-S3 podrá contradecir estos objetivos ni las fronteras de F0-S1; si
lo hiciera, se reportará como WARN o FAIL con documento y sección.

## 18. Relación con fases posteriores

F0-S2 es dirección; F1–F11 son diseño e implementación progresiva:

```text
F0-S2
Dirección y objetivos
```

```text
F1–F11
Diseño e implementación progresiva
```

F0-S2 no invade responsabilidades posteriores: no define Rules operativas,
diseño de Agents, Skills, Orchestrator, arquitectura técnica, CI/CD,
infraestructura, implementación, métricas definitivas de F11 ni diseño del
chatbot piloto de F10. La medición formal del objetivo aspiracional
corresponde principalmente a F10/F11.
