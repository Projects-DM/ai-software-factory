# SYSTEM-OVERVIEW — AI Software Factory — F0-S4 Arquitectura conceptual

Fase: F0 — Fundaciones.
Sprint: F0-S4 — Arquitectura conceptual.
Estado: diseño conceptual. No implementa la Factory.

Este documento define la visión general arquitectónica de AI Software
Factory: sus componentes principales, responsabilidades, relaciones,
límites y principios de interacción. Es el puente entre las fundaciones
(F0-S1, F0-S2, F0-S3) y el futuro diseño del flujo de trabajo (F0-S5).

Nivel: conceptual. No define tecnologías, infraestructura, Agents,
Skills, Rules operativas, Orchestrator funcional ni automatizaciones.

Documento complementario: `COMPONENTS.md` (ficha por componente).
Diagrama: `ai-software-factory-architecture.mmd` (representación visual).

## 1. Propósito arquitectónico

Dar una organización conceptual del sistema que permita:

- situar cada capacidad futura (F1–F11) en un componente con
  responsabilidad diferenciada;
- razonar sobre autonomía, control, evidencia y evolución antes de
  implementar nada;
- detectar qué falta, qué sobra y qué invade responsabilidades ajenas;
- responder a la pregunta de F0-S4: ¿qué componentes existen y cómo se
  relacionan?, preparando la pregunta de F0-S5: ¿cómo fluye el trabajo a
  través de esos componentes?

La arquitectura no ejecuta nada. Describe dónde ocurrirá cada cosa cuando
la Factory exista.

## 2. Visión general

AI Software Factory se organiza como una cadena de responsabilidad
supervisada por el humano:

```text
                    HUMAN
                      │
                      ▼
                    TASK
                      │
                      ▼
                    RULES
                      │
                      ▼
                ORCHESTRATOR
                  │       │
                  ▼       ▼
                AGENTS  CONTEXT
                  │       │
                  ▼       ▼
                SKILLS  KNOWLEDGE
                  │
                  ▼
                 TOOLS
                  │
                  ▼
              EXECUTION
                  │
                  ▼
              VALIDATION
                  │
                  ▼
               EVIDENCE
                  │
                  ▼
             TRACEABILITY
                  │
                  ▼
             MEASUREMENT
                  │
                  ▼
              EVOLUTION
```

El humano origina el trabajo (Task) y autoriza los límites (Rules). El
Orchestrator coordina, sin sustituir responsabilidades. Los Agents
ejecutan mediante Skills y Tools sobre un Execution acotado. Todo
resultado pasa por Validation, produce Evidence, se registra en
Traceability y alimenta Measurement y Evolution. Recovery atraviesa la
cadena como capacidad transversal de cada etapa.

Este modelo es una referencia conceptual, no una especificación rígida de
implementación. El orden lógico es el mostrado; el diseño detallado del
flujo (ramas, reintentos, estados) corresponde a F0-S5.

## 3. Componentes

Quince componentes con posición arquitectónica definida (fichas completas
en `COMPONENTS.md`):

| ID | Componente | Rol en una frase |
|----|-----------|------------------|
| C01 | Human | Autoridad final: origina, prioriza, autoriza y decide. |
| C02 | Task | Unidad de trabajo representable y trazable. |
| C03 | Rules | Límites y criterios operativos derivados de los principios. |
| C04 | Orchestrator | Coordina tareas, estados, agentes, validaciones y Human Gates. |
| C05 | Agents | Responsabilidades ejecutoras acotadas y separadas. |
| C06 | Context / Knowledge | Información necesaria y conocimiento versionado para ejecutar. |
| C07 | Skills | Procedimientos reutilizables validados. |
| C08 | Tools | Capacidades técnicas concretas sin autoridad propia. |
| C09 | Execution | Ejecución acotada dentro de límites y permisos. |
| C10 | Validation | Contraste del resultado contra criterios humanos. |
| C11 | Evidence | Prueba verificable de lo ejecutado y validado. |
| C12 | Traceability | Registro de extremo a extremo de origen, ejecución y resultado. |
| C13 | Recovery | Detección, contención, diagnóstico y recuperación o escalado. |
| C14 | Measurement | Comparación objetiva contra baseline para afirmar mejora. |
| C15 | Evolution | Cambio versionado del sistema basado en evidencia. |

Ningún componente concentra responsabilidades ajenas (ver riesgos R03,
R04). Ninguno existe todavía como implementación: son posiciones
arquitectónicas.

## 4. Relaciones

Relaciones estructurales (detalle por componente en `COMPONENTS.md`):

- Human → Task: el humano define y prioriza el trabajo; ningún otro
  componente crea objetivos por iniciativa propia.
- Task → Rules: cada tarea se ejecuta bajo las Rules aplicables; sin
  Rules no hay delegación legítima.
- Rules → Orchestrator: el Orchestrator solo coordina dentro de los
  límites que las Rules establecen.
- Orchestrator → Agents / Context: el Orchestrator asigna trabajo a
  Agents y provee a cada uno el contexto mínimo necesario (P12).
- Agents → Skills → Tools → Execution: el Agent ejecuta un
  procedimiento reutilizable (Skill) mediante capacidades técnicas
  (Tools) dentro de un Execution acotado.
- Execution → Validation: ningún resultado de ejecución avanza sin
  validación (P03); ejecutar ≠ éxito.
- Validation → Evidence: validar produce prueba (tests, revisiones,
  artefactos, logs, resultados de CI, verificaciones).
- Evidence → Traceability: la evidencia se registra vinculada a su
  origen (objetivo → plan → cambio → commit → test → review → PR → CI →
  merge → release → deploy, P13).
- Traceability → Measurement: solo lo trazado puede medirse
  objetivamente (P25).
- Measurement → Evolution: solo lo medido y validado puede motivar un
  cambio del sistema (P20, P26).
- Recovery ↔ todas las etapas: cada etapa puede detectar, detener,
  preservar evidencia y escalar (P14, P15).
- Evolution → Rules / Skills / Agents: la evolución actualiza los
  instrumentos bajo control humano y versionado (P19).

## 5. Flujo conceptual

El recorrido lógico de una unidad de trabajo:

1. Human define la Task con criterios de aceptación.
2. Las Rules aplicables acotan permisos, autonomía y validación exigida.
3. El Orchestrator planifica, asigna y atraviesa los Human Gates.
4. Los Agents ejecutan con el contexto mínimo necesario, vía Skills y
   Tools, dentro del Execution acotado.
5. Validation contrasta el resultado contra los criterios; el fallo
   activa Recovery (diagnosticar antes de repetir, P15).
6. El resultado validado genera Evidence y se inscribe en Traceability.
7. Measurement compara contra baseline cuando corresponde.
8. Evolution propone cambios al sistema solo con evidencia suficiente y
   aprobación humana.

El diseño detallado de estados, transiciones, reintentos y puertas
corresponde a F0-S5. Aquí solo se fija el orden lógico y las
dependencias: nada se salta Validation, nada avanza sin Evidence, nada
evoluciona sin Measurement.

## 6. Frontera Factory / Product

La arquitectura pertenece a la Factory, no a ningún Product (P29):

- los componentes C01–C15 describen cómo se construye software, nunca qué
  debe hacer una aplicación concreta;
- las necesidades particulares de un producto no definen ni modifican
  arbitrariamente componentes de la Factory;
- el piloto futuro (independiente de SGC-DM) será un usuario de esta
  arquitectura, no su definición;
- SGC-DM permanece fuera: ni código base, ni laboratorio permanente, ni
  referencia arquitectónica.

## 7. Modelo de autonomía

La autonomía opera por niveles ganados con evidencia (P26), nunca
presuntos. Referencia conceptual (F0-S2, sin declarar ningún nivel
alcanzado):

```text
Nivel 1 — Asistencia
Nivel 2 — Ejecución supervisada
Nivel 3 — Ejecución autónoma controlada
Nivel 4 — Ejecución autónoma condicionada
```

Reglas arquitectónicas:

- cada delegación vive dentro de Rules explícitas y reversibles (P01);
- capability ≠ authority: que un componente pueda ejecutar una acción no
  lo autoriza a ejecutarla;
- a mayor riesgo, irreversibilidad o impacto, mayor exigencia de
  validación y de presencia humana;
- el nivel efectivo de cada tipo de tarea se determinará con evidencia
  en fases de validación y medición, no por declaración.

## 8. Human Gates

Un Human Gate es un punto del flujo donde el avance requiere aprobación
humana explícita. La arquitectura reserva su posición lógica (el diseño
detallado de cada puerta corresponde a F0-S5 y sus reglas a F1):

- definición y priorización de la Task;
- ampliación de permisos o de autonomía delegada;
- decisiones irreversibles o costosas (P17);
- resultados que no superan Validation o que presentan ambigüedad
  significativa (P06);
- cualquier evolución del sistema (Rules, Skills, Agents, arquitectura).

Principio: ante excepción, ambigüedad o falta de evidencia, el control
vuelve al humano.

## 9. Propiedades arquitectónicas

La arquitectura, cuando se implemente, deberá exhibir estas propiedades
(hoy son exigencias de diseño, no capacidades existentes):

- verificabilidad: cada entrega contrasta contra criterios humanos;
- trazabilidad de extremo a extremo (P13);
- recuperabilidad: fallo seguro (P14) y recuperación diagnosticada
  (P15);
- least privilege: ningún componente dispone de más permisos que los
  necesarios (P09);
- minimización de contexto y de datos (P12, P24);
- reversibilidad preferente (P17) e idempotencia cuando sea viable
  (P16);
- simplicidad justificada: nada de lo que un mecanismo menor resuelva se
  convierte en componente mayor (P27);
- evolucionabilidad sin reconstrucción completa (P28);
- independencia tecnológica: ninguna tecnología concreta es premisa
  arquitectónica (P21); local-first antes que complejidad remota (P22).

## 10. Límites del diseño

Este diseño no incluye ni anticipa implementación de:

- Agents, Skills, Rules operativas u Orchestrator funcional;
- APIs, bases de datos, microservicios o infraestructura;
- CI/CD, deployment o automatizaciones funcionales;
- F10 (piloto) ni implementación de F11 (medición);
- diseño detallado de F1, F2, F3, F7 u otras fases futuras;
- reorganización masiva del repositorio.

Tampoco convierte conceptos en decisiones tecnológicas prematuras
(riesgos R01, R02, R09, R10). Cada exclusión es deliberada: la
arquitectura fija posiciones y relaciones, no tecnologías.

## 11. Relación con las fundaciones

- F0-S1 (identidad y alcance): la arquitectura organiza el sistema /
  proceso / instrumentación definido allí; respeta actores, autoridad
  diferenciada, fronteras y la exterioridad de SGC-DM. Coherencia: PASS.
- F0-S2 (objetivos y North Star): cada componente sirve a la North Star
  (autonomía progresiva, verificabilidad, trazabilidad, menos trabajo
  manual, control humano, recuperación, mejora continua); Measurement y
  Evolution se conciben como capacidades sin implementar F11 ni afirmar
  la hipótesis 20×–30×. Coherencia: PASS.
- F0-S3 (principios P01–P30): cada decisión arquitectónica importante
  cita su principio (ver sección 12 de `COMPONENTS.md`). Los principios
  no negociables (P01, P02, P03, P05, P06, P09, P13, P14, P23, P25, P26)
  tienen posición arquitectónica explícita. Coherencia: PASS.

## 12. Preparación para F0-S5

F0-S4 entrega a F0-S5:

- quince componentes con responsabilidad diferenciada y sin
  duplicaciones arbitrarias;
- un orden lógico de flujo con puntos de validación, evidencia y Human
  Gates reservados;
- la pregunta respondida (¿qué componentes existen y cómo se
  relacionan?) para que F0-S5 responda la suya (¿cómo fluye el trabajo a
  través de esos componentes?) sin redefinir la arquitectura.

F0-S4 no se adelanta al diseño detallado de estados y transiciones de
F0-S5.
