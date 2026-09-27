# SCOPE-BOUNDARIES — AI Software Factory — F0-S1 Fronteras de alcance

Fase: F0 — Fundaciones.
Sprint: F0-S1 — Definición de identidad y alcance.
Estado: conceptual y documental. No implementa la Factory.

Este documento define las fronteras explícitas de AI Software Factory.
Complementa a `PROJECT-SCOPE.md`. En caso de aparente contradicción,
prevalece la interpretación más restrictiva: lo no autorizado
explícitamente queda fuera del alcance actual.

## 1. Dentro del alcance

Pertenecen al alcance conceptual de la Factory los aspectos relacionados
con:

- proceso de ingeniería
- coordinación de trabajo
- agentes
- Skills
- Rules
- herramientas
- testing
- Git / GitHub
- CI/CD
- documentación
- evidencia
- trazabilidad
- observabilidad
- supervisión
- recuperación
- medición
- evolución

Aclaración: "dentro del alcance" significa dentro del alcance conceptual
y evolutivo de la Factory, no dentro de lo implementado en F0-S1. F0-S1
solo define identidad y alcance; no implementa ninguna de estas
capacidades.

## 2. Fuera del alcance actual

F0-S1 NO implementa:

- agentes funcionales
- Skills funcionales
- Rules operativas
- Orchestrator
- automatización compleja
- infraestructura distribuida
- sistemas remotos de supervisión
- producción autónoma
- aplicaciones de negocio
- chatbot piloto
- funcionalidades de SGC-DM

Tampoco implementa arquitectura de software detallada, contratos técnicos,
APIs, bases de datos, infraestructura ni automatizaciones. Eso corresponde
a fases posteriores y requerirá definición y aprobación humana explícita.

SGC-DM es una referencia externa de aprendizaje y evidencia del problema.
Queda fuera del alcance: no es código base de la Factory, no es un Product
de la Factory y no debe convertirse en su laboratorio permanente.

## 3. Factory vs Product

Separación inequívoca:

- Factory = sistema / proceso / instrumentación para construir software.
  Define cómo se trabaja: coordinación, validación, evidencia,
  trazabilidad, supervisión y evolución del propio proceso.
- Product = aplicación o producto concreto construido utilizando la
  Factory. Define qué se construye: objetivos, requisitos y valor de una
  aplicación determinada.

Consecuencias:

- ningún Product forma parte de la definición de la Factory;
- la Factory no hereda requisitos, código ni decisiones de ningún Product
  pasado o futuro;
- el primer proyecto piloto será un Product independiente de SGC-DM y se
  definirá en una fase posterior;
- los criterios de aceptación de un Product los define el humano, no la
  Factory por iniciativa propia.

## 4. Límites de autonomía

Principio: Capability ≠ Authority.

La capacidad técnica de ejecutar una acción no implica autorización para
ejecutarla.

Esto implica:

- un agente o herramienta puede ser capaz de modificar código, Git, CI/CD
  o documentación sin estar autorizado a hacerlo;
- toda delegación requiere autorización humana explícita, límites definidos
  y posibilidad de reversión;
- la autonomía solo aumenta mediante evidencia, validación y límites
  conocidos (ver `PROJECT-SCOPE.md`, sección 6);
- ante excepciones, ausencia de evidencia o ambigüedad, el control vuelve
  al humano.

No se promete autonomía total. La producción autónoma queda fuera del
alcance.

## 5. Límites humanos

Permanecen bajo control humano, sin excepción en F0-S1 y como requisito
evolutivo de la Factory:

- objetivos
- prioridades
- decisiones arquitectónicas
- permisos sensibles
- criterios de aceptación
- riesgos
- excepciones
- decisiones críticas
- evolución de la propia Factory

Ningún agente, Skill, Rule, herramienta u automatización futura puede
redefinir estos límites, ampliar su propia autoridad ni modificar la
Factory sin aprobación humana explícita.

## 6. Límites tecnológicos

No se asume ninguna tecnología futura como obligatoria. No se definen en
F0-S1 decisiones de implementación, stack, infraestructura, bases de datos,
APIs ni orquestadores.

OpenCode y GitHub forman parte del entorno actual de trabajo, pero la
arquitectura futura debe permanecer abierta a evolución basada en
evidencia. La adopción, sustitución o ampliación de tecnologías requerirá
justificación, validación y aprobación humana en fases posteriores.

## 7. Límites de alcance temporal

Se distinguen tres planos, que no deben confundirse:

- Estado actual (F0-S1): definición conceptual y documental de identidad
  y alcance. Sin código funcional, sin agentes, sin Skills, sin Rules
  operativas, sin automatización.
- Capacidades previstas: las listadas en `PROJECT-SCOPE.md`, sección 5
  y en este documento, sección 1. Son dirección evolutiva, no compromiso
  de implementación ni diseño anticipado.
- Capacidades futuras: cualquier evolución posterior (incluido el piloto
  independiente de SGC-DM). Se definirá en su fase correspondiente.

No se describen planes futuros como funcionalidades implementadas. Ningún
documento de F0-S1 debe leerse como especificación de F0-S2 o sprints
posteriores.
