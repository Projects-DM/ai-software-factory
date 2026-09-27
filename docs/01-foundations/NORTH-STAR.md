# NORTH-STAR — AI Software Factory — F0-S2 Estrella del Norte

Fase: F0 — Fundaciones.
Sprint: F0-S2 — Objetivos y North Star.
Estado: conceptual y documental. No implementa la Factory.

Esta North Star es la referencia estable para decisiones futuras. No
describe una capacidad implementada ni validada. Toda lectura que la
interprete como estado actual es incorrecta.

Documento complementario: `OBJECTIVES.md` (objetivos estratégicos).
Base obligatoria: `PROJECT-SCOPE.md` y `SCOPE-BOUNDARIES.md` (F0-S1).

## 1. Definición formal de North Star

> **Construir un sistema de ingeniería de software progresivamente autónomo, verificable y trazable que permita al desarrollador entregar soluciones de calidad con menos trabajo manual, manteniendo control humano, capacidad de recuperación y mejora continua.**

Esta definición es oficial. No se cambia su significado en este ni en
otros documentos.

## 2. Interpretación

Cada término de la definición es normativo:

- "sistema de ingeniería": no una herramienta aislada ni una aplicación
  de negocio, sino el sistema / proceso / instrumentación definido en
  F0-S1;
- "progresivamente autónomo": la autonomía se gana por evidencia y por
  niveles, nunca se presume;
- "verificable": toda entrega se contrasta contra criterios de aceptación
  humanos con evidencia comprobable;
- "trazable": toda decisión y cambio se rastrea de objetivo a registro
  Git;
- "menos trabajo manual": menos coordinación manual, menos reconstrucción
  de contexto y menos rework evitable;
- "manteniendo control humano, capacidad de recuperación y mejora
  continua": estas tres condiciones son invariantes; si faltan, el avance
  no cuenta como progreso hacia la North Star.

## 3. Autonomía progresiva

La North Star exige autonomía progresiva, no autonomía inmediata ni total.
Evolución conceptual de referencia (ningún nivel se declara alcanzado):

```text
Nivel 1 — Asistencia
Nivel 2 — Ejecución supervisada
Nivel 3 — Ejecución autónoma controlada
Nivel 4 — Ejecución autónoma condicionada
```

Implicaciones:

- autonomía no significa ausencia de control;
- capability ≠ authority;
- la autonomía se gana mediante evidencia;
- las acciones críticas continúan sujetas a límites y Human Gates;
- el nivel real alcanzado deberá determinarse posteriormente mediante
  evidencia, principalmente en fases de validación y medición.

## 4. Verificabilidad

Un resultado orientado a la North Star solo es válido si puede
verificarse: criterios de aceptación definidos por el humano, pruebas y
revisión estructuradas, evidencia accesible. Lo no verificable no cuenta
como avance, aunque sea rápido. Rige `IMPLEMENTED ≠ VALIDATED`: que algo
se haya ejecutado no significa que esté validado.

## 5. Trazabilidad

La trazabilidad es la condición que hace auditables la verificabilidad,
la autonomía y la medición: objetivo → especificación → implementación →
prueba → revisión → documentación → Git. Sin trazabilidad no hay forma de
saber qué se hizo, por qué, con qué autorización ni cómo revertirlo.

## 6. Reducción del trabajo manual

La dirección es reducir el trabajo manual del desarrollador sobre el ciclo
completo de ingeniería, con objetivo aspiracional 20×–30× formulado como
hipótesis (ver sección 11). Esta reducción se refiere a tiempo humano
sobre trabajo comparable:

```text
Throughput Improvement =
Tiempo humano baseline
────────────────────────
Tiempo humano con Factory
```

Condiciones: es hipótesis aspiracional, objetivo futuro, no demostrado
actualmente, no garantía, no métrica aislada, sujeto a medición sobre
trabajo comparable y acompañado por indicadores de calidad,
trazabilidad, errores, rework, intervención y recuperación. La medición
formal corresponde principalmente a F10/F11. No se afirma que la Factory
actualmente consiga 20×–30× ni ningún valor parcial. Rige
`ASPIRATIONAL ≠ ACHIEVED`.

## 7. Calidad

La calidad es parte de la definición ("soluciones de calidad") y condición
de validez de la productividad:

```text
Productividad
+
Calidad
+
Trazabilidad
+
Control
+
Recuperación
```

Una mejora de velocidad acompañada de degradación significativa de calidad
no constituye por sí misma una mejora válida del sistema. La calidad se
evaluará junto a trazabilidad, errores, rework, intervención humana y
recuperación, nunca como velocidad aislada.

## 8. Control humano

El control humano es invariante de la North Star. El humano conserva:
objetivos, prioridades, decisiones arquitectónicas, permisos sensibles,
criterios de aceptación, riesgos, excepciones, decisiones críticas y
evolución de la propia Factory. Ninguna delegación amplía sus propios
límites sin aprobación humana explícita.

## 9. Recuperación

"Capacidad de recuperación" significa poder volver a un estado conocido y
válido ante errores o excepciones, diagnosticar con evidencia y contener el
daño dentro de límites. Un sistema que avanza rápido pero no se recupera
se aleja de la North Star, no se acerca a ella.

## 10. Mejora continua

"Mejora continua" opera en dos planos inseparables:

- mejora del sistema (proceso, instrumentos y criterios cada vez más
  precisos y validados);
- mejora del desarrollador (mejor criterio, mejores especificaciones,
  mejores decisiones).

Por ello la Factory debe funcionar progresivamente como sistema de
producción, laboratorio de ingeniería, entorno de aprendizaje y sistema de
mejora continua. La reutilización (convertir procedimientos en Rules,
Skills, Agents, scripts o workflows) debe evaluarse antes de formalizarse;
no todo procedimiento debe automatizarse.

## 11. Productividad

Productividad hacia la North Star = entregar soluciones de calidad con
menos trabajo manual, de forma verificable, trazable, controlada y
recuperable. No se reduce a velocidad. El objetivo aspiracional 20×–30× se
conserva explícitamente como hipótesis aspiracional, objetivo futuro, no
demostrado, no garantía, no métrica aislada, sujeto a medición sobre
trabajo comparable y acompañado por los indicadores de la sección 6. Su
medición formal corresponde principalmente a F10/F11.

## 12. Principios implícitos

La North Star presupone, sin sustituir a F0-S3 (que los definirá
formalmente):

- evidencia antes que delegación;
- límites explícitos y reversibles;
- verificación antes que celebración (`IMPLEMENTED ≠ VALIDATED`);
- aspiración antes que afirmación (`ASPIRATIONAL ≠ ACHIEVED`);
- humano como autoridad final;
- reutilización evaluada, no automática;
- ningún atajo de velocidad a costa de calidad, trazabilidad, control o
  recuperación.

## 13. Relación con OBJECTIVES.md

`OBJECTIVES.md` desarrolla esta North Star en objetivos estratégicos,
criterios generales de éxito y dirección de evolución. La North Star es la
referencia estable; los objetivos son su despliegue operativo. Ambos
documentos son coherentes entre sí: todo objetivo deriva del propósito de
F0-S1 y apunta a la definición formal de la sección 1. Coherencia
OBJECTIVES ↔ NORTH-STAR: PASS (ver validación final del sprint).

## 14. Relación con F0-S1

```text
F0-S1
¿Qué somos?
¿Qué problema resolvemos?
¿Qué está dentro?
¿Qué está fuera?
        ↓
F0-S2
¿Qué queremos conseguir?
¿Hacia dónde evolucionamos?
¿Cómo definimos éxito?
```

F0-S2 no contradice F0-S1: mantiene identidad Factory vs Product,
problema de coordinación, actores con autoridad diferenciada, fronteras
explícitas, SGC-DM como referencia externa y piloto futuro independiente.
Coherencia F0-S1 ↔ F0-S2: PASS.

## 15. Relación con F0-S3

```text
F0-S2
¿Qué queremos conseguir?
¿Hacia dónde evolucionamos?
¿Cómo definimos éxito?
        ↓
F0-S3
¿Qué principios guiarán las decisiones?
```

F0-S3 deberá derivar sus principios de esta North Star y de
`OBJECTIVES.md`, sin contradecirlos. Preparación para F0-S3: PASS; F0-S3
queda pendiente de definición y no se anticipa en este sprint.

## 16. Relación con F10

F10 es la fase de validación prevista donde el piloto independiente de
SGC-DM y la medición sobre trabajo comparable deberán aportar la primera
evidencia formal del avance hacia la North Star (incluido el contraste de
la hipótesis 20×–30× con indicadores de calidad, errores, rework,
intervención y recuperación). F0-S2 no diseña el chatbot piloto ni
anticipa resultados de F10.

## 17. Relación con F11

F11 es la fase de medición y evolución prevista donde se consolidará la
medición formal (métricas definitivas, aún no definidas en F0-S2) y la
mejora continua basada en evidencia. F0-S2 no define métricas definitivas
de F11; solo establece la dirección que F11 deberá medir.

## 18. Dirección de evolución

La evolución hacia la North Star es progresiva y condicionada:

```text
F0-S2
Dirección y objetivos
```

```text
F1–F11
Diseño e implementación progresiva
```

F0-S2 no crea Rules operativas, diseño de Agents, Skills, Orchestrator,
arquitectura técnica, CI/CD, infraestructura ni implementación. Cada paso
posterior deberá justificarse contra esta North Star, validarse con
evidencia y mantenerse reversible bajo control humano. Lo no validado no
cuenta como progreso.
