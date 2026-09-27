# PROJECT-SCOPE — AI Software Factory — F0-S1 Identidad y alcance

Fase: F0 — Fundaciones.
Sprint: F0-S1 — Definición de identidad y alcance.
Estado: conceptual y documental. No implementa la Factory.

Este documento define la identidad, el propósito, el problema, los actores,
el alcance conceptual, la autonomía progresiva, el control humano y la
separación Factory vs Product. No define arquitectura, implementación ni
automatización.

Documento complementario: `SCOPE-BOUNDARIES.md` (fronteras explícitas).

## 1. Identidad

AI Software Factory (la Factory) es un sistema profesional de ingeniería de
software asistida y progresivamente automatizada mediante IA, GitHub,
OpenCode, agentes especializados, Rules, Skills, herramientas, testing,
CI/CD, observabilidad, orquestación y supervisión humana.

La Factory no es una aplicación de negocio. Es el sistema / proceso /
instrumentación que permite representar, contextualizar, ejecutar, validar,
evidenciar y trazar trabajo de ingeniería de forma estructurada.

Referencia de origen: el proyecto SGC-DM es una referencia de aprendizaje y
evidencia del problema que origina la Factory. SGC-DM no forma parte de la
Factory, no es su código base y no debe convertirse en su laboratorio
permanente.

## 2. Propósito

La Factory existe para transformar la forma de desarrollar software: pasar
de un modelo donde una persona coordina manualmente múltiples herramientas
e interacciones con IA, a un sistema de ingeniería donde el trabajo puede
representarse, contextualizarse, ejecutarse, validarse, evidenciarse y
trazarse de forma estructurada.

La transformación buscada no es únicamente producir código más rápido, sino
sistematizar el proceso de ingeniería para hacerlo repetible, revisable,
recuperable, medible y evolutivo, manteniendo la supervisión humana sobre
las decisiones críticas.

## 3. Problema

El problema actual es la coordinación manual entre humano, IA, herramientas,
código, pruebas, documentación y Git.

En el modelo actual, una persona debe:

- repartir contexto entre herramientas e interacciones con IA inconexas;
- recordar objetivos, prioridades, decisiones y criterios de aceptación;
- coordinar manualmente análisis, implementación, testing, revisión,
  documentación y operaciones Git/GitHub;
- reconstruir evidencia y trazabilidad a posteriori;
- gestionar excepciones, riesgos y permisos sin un marco explícito;
- sostener la calidad y la coherencia del proceso en ausencia de un sistema
  que lo represente.

El resultado es un proceso frágil, poco trazable, difícil de validar,
difícil de recuperar ante errores y difícil de evolucionar de forma
controlada. El problema central es, por tanto, la coordinación y
sistematización del proceso de ingeniería, no la velocidad de escritura
de código.

## 4. Usuarios y actores

Se distinguen los siguientes actores. No tienen la misma autoridad.

### Human / Technical Director

Persona responsable del sistema. Define objetivos, prioridades,
arquitectura, permisos, criterios de aceptación, riesgos, excepciones y
decisiones críticas. Supervisa y aprueba la evolución de la propia Factory.
Es la única autoridad final. Ver sección 7.

### Factory

El sistema / proceso / instrumentación para construir software: reglas de
trabajo, coordinación, validación, evidencia, trazabilidad, medición y
evolución. No es un agente individual ni una aplicación de negocio.

### Product

La aplicación o producto concreto construido utilizando la Factory. Cada
Product tiene sus propios objetivos, requisitos y criterios de aceptación.
El primer proyecto piloto será independiente de SGC-DM y se definirá en una
fase posterior.

### AI agents

Agentes que ejecutan trabajo de ingeniería asistido dentro de los límites
definidos por el humano y la Factory. No tienen autoridad propia sobre
objetivos, permisos sensibles, arquitectura ni decisiones críticas. Su
autonomía es progresiva y condicionada (ver sección 6).

### Tools

Herramientas utilizadas durante el proceso de ingeniería (por ejemplo,
testing, revisión, documentación, medición). Ejecutan capacidades técnicas
concretas. No definen objetivos ni autorizan acciones por sí mismas.

### Git / GitHub

Sistema de registro y control de versiones del trabajo y la evidencia.
Soporta trazabilidad, revisión y recuperación. No sustituye la decisión
humana.

### OpenCode

Entorno actual de trabajo asistido por IA. Forma parte del entorno de
trabajo presente, no de una arquitectura futura obligatoria. La arquitectura
futura de la Factory debe permanecer abierta a evolución basada en
evidencia (ver `SCOPE-BOUNDARIES.md`).

## 5. Alcance

La Factory pretende soportar progresivamente las siguientes capacidades:

- análisis
- planificación
- especificación
- implementación
- testing
- revisión
- documentación
- Git
- CI/CD
- evidencia
- trazabilidad
- recuperación
- medición
- evolución

Aclaración obligatoria: estas capacidades se incorporarán progresivamente
y no deben presentarse como ya implementadas. F0-S1 no implementa ninguna
de ellas; solo define la identidad y el alcance conceptual que permitirá
desarrollarlas en fases posteriores bajo control humano y con evidencia.

## 6. Autonomía progresiva

La autonomía en la Factory es progresiva: se gana mediante evidencia,
validación y límites conocidos.

Esto significa:

- ninguna capacidad se considera autónoma por el hecho de ser técnicamente
  posible;
- cada incremento de autonomía requiere validación previa y criterios de
  aceptación definidos por el humano;
- cada delegación opera dentro de límites explícitos y reversibles;
- la falta de evidencia o la aparición de excepciones devuelve el control
  al humano.

No se afirma que la Factory será completamente autónoma. La autonomía total
no es un objetivo declarado de este proyecto.

Principio aplicable: Capability ≠ Authority. Ver `SCOPE-BOUNDARIES.md`.

## 7. Control humano

El humano (Human / Technical Director) conserva el control sobre:

- objetivos
- prioridades
- decisiones arquitectónicas
- permisos sensibles
- criterios de aceptación
- riesgos
- excepciones
- decisiones críticas
- evolución de la propia Factory

Ningún agente, herramienta, automatización o proceso de la Factory puede
asumir estas responsabilidades por iniciativa propia ni modificar sus
propios límites sin aprobación humana explícita.

## 8. Factory vs Product

- Factory = sistema / proceso / instrumentación para construir software.
- Product = aplicación o producto concreto construido utilizando la Factory.

La Factory define cómo se trabaja (proceso, coordinación, validación,
evidencia, trazabilidad). El Product define qué se construye (objetivos,
requisitos y valor de negocio de una aplicación concreta).

SGC-DM no es la Factory ni un Product de la Factory; es una referencia
externa de aprendizaje. El piloto futuro será un Product independiente y
se definirá en fase posterior.

## 9. Estado actual

El proyecto se encuentra en fase F0 — Fundaciones.

F0-S1 corresponde exclusivamente a la definición de identidad y alcance
contenida en este documento y en `SCOPE-BOUNDARIES.md`.

No existe todavía código funcional, arquitectura técnica, agentes, Skills,
Rules, scripts ni automatización de la Factory. Ninguna capacidad futura
descrita en este documento debe interpretarse como capacidad existente.
