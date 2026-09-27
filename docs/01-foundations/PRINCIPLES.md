# PRINCIPLES — AI Software Factory — F0-S3 Principios

Fase: F0 — Fundaciones.
Sprint: F0-S3 — Principios.
Estado: conceptual y documental. No implementa la Factory.

Este documento define los principios fundamentales que orientan el diseño,
construcción, evolución y operación de AI Software Factory. Es el nivel
conceptual que conecta la identidad y los objetivos (F0-S1, F0-S2) con las
reglas operativas que se desarrollarán posteriormente en F1 — Rules.

Establece cómo debe pensar y evolucionar la Factory. No define
procedimientos detallados, permisos específicos, workflows técnicos ni
reglas operativas exhaustivas: eso corresponde a F1 y fases posteriores.

Documentos base: `PROJECT-SCOPE.md` y `SCOPE-BOUNDARIES.md` (F0-S1),
`OBJECTIVES.md` y `NORTH-STAR.md` (F0-S2).

## 1. Propósito

Dar un marco conceptual estable para tomar decisiones coherentes sobre
arquitectura, automatización, Agents, Skills, herramientas, testing,
Git/GitHub, CI/CD, orquestación, observabilidad, supervisión y evolución,
preservando la identidad, la dirección y los límites definidos en F0-S1 y
F0-S2 mientras la Factory evoluciona.

Sin principios explícitos, cada regla operativa futura carecería de fuente
conceptual común y las decisiones de diseño quedarían a criterio del
momento.

## 2. Definición de principio

Un principio de AI Software Factory es una orientación fundamental y
relativamente estable para tomar decisiones sobre arquitectura,
automatización, Agents, Skills, herramientas, testing, Git/GitHub, CI/CD,
orquestación, observabilidad, supervisión y evolución.

Un principio no es una instrucción técnica detallada. La separación
conceptual, que deberá mantenerse durante la evolución de la Factory, es:

```text
PRINCIPIO
↓
Orientación fundamental

RULE
↓
Regla operativa concreta

SKILL
↓
Procedimiento reutilizable

AGENT
↓
Responsabilidad ejecutora
```

## 3. Relación con F0-S1

F0-S3 preserva F0-S1 sin contradecirlo:

- identidad: Factory = sistema / proceso / instrumentación para construir
  software; Product = aplicación concreta construida con la Factory;
- problema central: coordinación y sistematización del proceso de
  ingeniería, no "escribir código más rápido";
- actores con autoridad diferenciada y humano como única autoridad final;
- fronteras: F0-S3 no implementa agentes funcionales, Skills funcionales,
  Rules operativas, Orchestrator, automatización compleja, infraestructura,
  producción autónoma ni piloto; SGC-DM sigue siendo referencia externa,
  fuera de la Factory.

Si se detectara una contradicción con F0-S1, no se corrige
silenciosamente: se clasifica como PASS / WARN / FAIL indicando documento
y sección. En esta revisión: coherencia con F0-S1 = PASS.

## 4. Relación con F0-S2

F0-S3 deriva de F0-S2 sin contradecirlo:

- la North Star oficial ("sistema de ingeniería de software
  progresivamente autónomo, verificable y trazable...") es la referencia
  estable; los principios son su despliegue en criterios de decisión;
- los objetivos estratégicos de `OBJECTIVES.md` (verificabilidad,
  trazabilidad, autonomía condicionada a evidencia, recuperación,
  conocimiento reutilizable justificado, aprendizaje) se traducen aquí en
  principios operativos conceptuales;
- el objetivo aspiracional 20×–30× sigue siendo hipótesis no demostrada
  (ASPIRATIONAL ≠ ACHIEVED) y la medición formal sigue correspondiendo a
  F10/F11 (P25 desarrolla esta dirección sin definir métricas);
- IMPLEMENTED ≠ VALIDATED rige todo aumento de autonomía (P26).

Coherencia con F0-S2 = PASS.

## 5. Principios fundamentales

Los 30 principios siguientes son orientación fundamental, no reglas
operativas. Su traducción a Rules corresponde a F1.

## P01 — Máxima autonomía dentro de límites conocidos

La Factory deberá buscar el máximo nivel de autonomía que pueda alcanzarse
de forma segura, verificable y controlada dentro de límites explícitamente
conocidos.

La autonomía no deberá considerarse un objetivo absoluto. Deberá estar
condicionada por riesgo, evidencia, confiabilidad, permisos, capacidad de
recuperación y tipo de tarea.

Conceptualmente:

```text
Autonomía
+
Límites conocidos
+
Evidencia
+
Control
```

## P02 — El humano conserva el control de las decisiones críticas

La Factory deberá aumentar la capacidad de ejecución de la IA sin eliminar
la responsabilidad humana sobre decisiones que requieran criterio,
autorización o conocimiento contextual.

Deberán existir mecanismos para detener, aprobar, rechazar o modificar una
ejecución cuando sea necesario.

El objetivo no es eliminar al desarrollador. El objetivo es eliminar la
necesidad de intervención humana en actividades que puedan ejecutarse de
forma segura y verificable.

## P03 — Evidencia antes de avanzar

Ningún resultado deberá considerarse válido únicamente porque un Agent,
herramienta o modelo declare que está terminado. El avance entre estados
deberá sustentarse progresivamente en evidencia adecuada: tests,
revisiones, artefactos, logs, resultados de CI, criterios de aceptación,
verificaciones automatizadas, evidencia de ejecución.

Conceptualmente:

```text
Ejecutar
↓
Producir resultado
↓
Obtener evidencia
↓
Verificar
↓
Avanzar
```

## P04 — Calidad y velocidad deben evolucionar juntas

La Factory no deberá optimizar velocidad sacrificando sistemáticamente la
calidad. Una mejora de productividad solamente será significativa si
mantiene condiciones aceptables de calidad, mantenibilidad, seguridad,
trazabilidad y confiabilidad.

```text
Más rápido
≠
automáticamente mejor
```

La Factory deberá buscar:

```text
Productividad
+
Calidad
+
Control
```

## P05 — No arreglar una cosa rompiendo otra

Toda modificación deberá considerar su impacto sobre el sistema existente.
Antes de aceptar un cambio deberá evaluarse, según corresponda,
funcionalidad existente, dependencias, pruebas, arquitectura,
documentación, configuración, integraciones y despliegue. Los cambios
deberán minimizar regresiones y preservar comportamientos válidos salvo
que su modificación forme parte explícita del objetivo.

## P06 — No inventar requisitos

La Factory no deberá convertir suposiciones en requisitos. Cuando exista
ambigüedad significativa deberá: identificarla, determinar su impacto,
solicitar aclaración cuando sea necesaria, documentar la decisión y
continuar solamente cuando exista suficiente claridad.

El sistema deberá distinguir entre:

```text
Requisito confirmado
Suposición
Hipótesis
Decisión
Recomendación
```

Estos conceptos no deberán mezclarse.

## P07 — Reutilizar antes de crear

Antes de crear una nueva Skill, Agent, script, workflow, herramienta,
automatización o componente, deberá evaluarse si ya existe una capacidad
adecuada. La secuencia preferida será:

```text
Buscar
↓
Evaluar existente
↓
Reutilizar
↓
Adaptar si es necesario
↓
Crear solamente si aporta valor
```

## P08 — Automatizar solamente cuando exista valor

La automatización no será considerada valiosa simplemente por eliminar una
acción manual. Deberá aportar uno o varios beneficios verificables:
reducción de trabajo, reducción de errores, aumento de velocidad, aumento
de calidad, mejora de trazabilidad, capacidad nueva, mejor recuperación,
continuidad operativa o reutilización. Una automatización cuyo costo de
mantenimiento supere su beneficio deberá poder ser reconsiderada.

## P09 — Least Privilege

Cada componente deberá disponer únicamente de los permisos necesarios para
cumplir su responsabilidad. Esto deberá aplicarse progresivamente a Agents,
Skills, scripts, herramientas, Git, GitHub, integraciones y ejecución
remota.

Conceptualmente:

```text
Responsabilidad
↓
Permisos necesarios
↓
Nada más
```

Este principio será desarrollado con mayor detalle posteriormente en F1,
F3, F6 y F9.

## P10 — Separación de responsabilidades

Las diferentes capacidades de la Factory deberán mantenerse separadas
cuando exista una razón clara para ello. Ejemplos:

```text
Planner
≠
Implementer
```

```text
Implementer
≠
Reviewer
```

```text
Testing
≠
Declaración de éxito del código
```

```text
Orchestrator
≠
Programación del producto
```

La separación deberá permitir menor acoplamiento, mejor validación, mayor
trazabilidad, menor riesgo, reutilización y evolución independiente.

## P11 — El Orchestrator coordina; no sustituye responsabilidades

La futura capa de orquestación deberá coordinar tareas, estados, Agents,
Skills, contexto, validaciones, recuperación y Human Gates. No deberá
convertirse en un componente monolítico que contenga toda la lógica de la
Factory.

> **El Orchestrator coordina; los componentes especializados ejecutan sus responsabilidades.**

La arquitectura concreta será definida posteriormente.

## P12 — Contexto mínimo necesario

Cada Agent o componente deberá recibir el contexto necesario para realizar
su trabajo, evitando cargar información irrelevante cuando pueda afectar a
precisión, costo, velocidad, seguridad o mantenibilidad.

Conceptualmente:

```text
Contexto disponible
↓
Contexto relevante
↓
Contexto necesario
```

La minimización de contexto deberá equilibrarse con la necesidad de
proporcionar información suficiente para evitar errores.

## P13 — Trazabilidad de extremo a extremo

Las actividades relevantes de la Factory deberán poder relacionarse con su
origen, ejecución, validación y resultado. La relación conceptual será:

```text
Objetivo
↓
Trabajo
↓
Plan
↓
Cambio
↓
Commit
↓
Test
↓
Review
↓
PR
↓
CI
↓
Merge
↓
Release
↓
Deploy
```

La trazabilidad deberá formar parte de la arquitectura y no agregarse
únicamente al final.

## P14 — Fallar de forma segura

Cuando una ejecución no pueda continuar correctamente, la Factory deberá
preferir:

```text
Detectar
↓
Detener o aislar
↓
Preservar evidencia
↓
Diagnosticar
↓
Recuperar o escalar
```

en lugar de continuar ciegamente. Un fallo controlado es preferible a una
ejecución aparentemente exitosa que produzca consecuencias desconocidas.

## P15 — Recuperar antes de repetir ciegamente

Ante un fallo, la Factory deberá intentar comprender su causa antes de
ejecutar nuevamente una operación potencialmente problemática. La
recuperación deberá considerar tipo de error, estado anterior, cambios
realizados, evidencia disponible, posibilidad de repetir de forma segura,
idempotencia e impacto de un segundo intento.

Conceptualmente:

```text
FAIL
↓
DIAGNOSE
↓
SAFE RETRY?
├── YES → RETRY
└── NO  → RECOVER / ESCALATE
```

## P16 — Idempotencia cuando sea posible

Las operaciones automatizadas deberán diseñarse, cuando sea técnicamente
viable, para que repetir una operación segura no produzca consecuencias
inesperadas. Este principio será especialmente relevante para workflows,
automatizaciones, GitHub, despliegues, comandos remotos, recuperación y
orquestación. No todas las operaciones podrán ser completamente
idempotentes, por lo que las excepciones deberán identificarse
explícitamente.

## P17 — Decisiones reversibles cuando sea posible

Cuando existan varias alternativas razonables, deberá preferirse una
solución que permita corregir o revertir decisiones sin generar costos
innecesarios. Esto no significa evitar decisiones permanentes. Significa
reconocer:

```text
Decisión reversible
≠
Decisión irreversible
```

Las decisiones irreversibles o costosas deberán recibir mayor análisis y,
cuando corresponda, aprobación humana.

## P18 — Documentar el conocimiento importante

El conocimiento crítico no deberá permanecer únicamente en conversaciones,
memoria individual, sesiones temporales o contexto de un modelo. Deberá
trasladarse progresivamente a artefactos versionados.

> **Si el conocimiento es necesario para repetir correctamente una actividad, debe existir una forma de conservarlo.**

## P19 — Versionar el conocimiento

Los documentos, Rules, Skills, Agents, workflows y decisiones relevantes
deberán poder evolucionar mediante control de versiones. Las
modificaciones significativas deberán conservar qué cambió, cuándo cambió,
por qué cambió, qué impacto tuvo y qué evidencia motivó el cambio. Git
será una pieza fundamental de este principio.

## P20 — La arquitectura debe evolucionar mediante evidencia

Las decisiones arquitectónicas no deberán modificarse únicamente por moda
tecnológica o disponibilidad de una herramienta. Una evolución deberá
justificarse mediante necesidad, evidencia, limitación actual, riesgo,
costo, beneficio, mantenibilidad e impacto. La arquitectura deberá
evolucionar cuando el sistema lo necesite.

## P21 — Herramientas al servicio del sistema

La Factory no deberá construirse alrededor de una herramienta específica.
OpenCode, GitHub, modelos de IA, APIs, servicios externos u otras
herramientas serán componentes reemplazables cuando exista una razón para
ello. La pregunta principal será:

> **¿Qué capacidad necesita la Factory?**

y después:

> **¿Qué herramienta permite proporcionarla de manera adecuada?**

No al contrario.

## P22 — Local-first antes de complejidad remota

La Factory deberá priorizar inicialmente una arquitectura local-first
cuando sea suficiente para validar las capacidades fundamentales. La
infraestructura remota deberá incorporarse progresivamente cuando exista
una necesidad real de supervisión, ejecución prolongada, disponibilidad,
colaboración, notificaciones u operación distribuida. La complejidad
remota no deberá introducirse antes de que exista una necesidad
justificada.

## P23 — Seguridad por diseño

La seguridad deberá considerarse desde el diseño y no únicamente después
de implementar una capacidad. Deberán considerarse progresivamente
permisos, secretos, autenticación, autorización, aislamiento, exposición
de datos, acciones destructivas, integraciones externas y operaciones
productivas. La seguridad deberá integrarse en la arquitectura de la
Factory.

## P24 — Privacidad y minimización de datos

La Factory deberá procesar únicamente la información necesaria para
realizar una tarea. La observabilidad, documentación y comunicación entre
componentes deberán evitar registrar o transmitir innecesariamente
secretos, tokens, credenciales, información privada, datos sensibles o
contenido no requerido. La necesidad de conservar información deberá
evaluarse frente a su riesgo.

## P25 — Medir antes de afirmar mejora

Una modificación no deberá considerarse una mejora simplemente porque
parece más rápida, más limpia, más autónoma o más automatizada. Cuando sea
posible, deberá existir una comparación objetiva:

```text
Baseline
↓
Cambio
↓
Medición
↓
Comparación
↓
Conclusión basada en evidencia
```

Este principio será fundamental para F11.

## P26 — Autonomía ganada mediante evidencia

La Factory no deberá recibir mayor autonomía únicamente porque una
capacidad haya sido implementada. Para aumentar autonomía deberá existir
evidencia suficiente sobre confiabilidad, calidad, comportamiento
esperado, capacidad de recuperación, trazabilidad y cumplimiento de
límites.

Conceptualmente:

```text
Capacidad
↓
Ejecuciones
↓
Evidencia
↓
Validación
↓
Mayor autonomía
```

## P27 — Mantener la simplicidad necesaria

La Factory deberá evitar complejidad que no produzca valor. No se deberá
crear un Agent cuando una Skill sea suficiente, un servicio cuando un
script sea suficiente, un Orchestrator cuando un workflow sea suficiente,
una integración cuando una herramienta existente sea suficiente, ni una
capa de abstracción sin necesidad demostrada. La complejidad deberá
justificarse por una necesidad real.

## P28 — Diseñar para evolución

Los componentes de la Factory deberán diseñarse considerando que las
herramientas pueden cambiar, los modelos pueden cambiar, los Agents
evolucionarán, las Skills serán versionadas, los workflows serán
modificados y los requisitos podrán cambiar. La arquitectura deberá
permitir evolución sin exigir reconstrucción completa del sistema.

## P29 — Separar Factory de producto

Las reglas, objetivos y mecanismos internos de AI Software Factory deberán
mantenerse conceptualmente separados de las reglas funcionales de los
productos construidos mediante ella.

```text
FACTORY
¿Cómo construimos software?
        │
        ▼
PRODUCTO
¿Qué debe hacer el software?
```

El comportamiento específico de un producto no deberá modificar
arbitrariamente el comportamiento operativo de la Factory.

## P30 — El aprendizaje forma parte del resultado

Una ejecución deberá producir no solamente software, sino también
conocimiento reutilizable cuando sea relevante. Después de una ejecución
importante deberá poder preguntarse: ¿qué funcionó?, ¿qué falló?, ¿qué fue
manual?, ¿qué pudo automatizarse?, ¿qué conocimiento debemos conservar?,
¿qué debería convertirse en Skill?, ¿qué Rule debería cambiar?, ¿qué
debería permanecer bajo control humano? Este principio conecta
directamente la operación de la Factory con F11.

## 6. Jerarquía conceptual

Los principios se entienden dentro de la siguiente cadena, que evita que
cada componente desarrolle sus propias reglas sin fuente común:

```text
NORTH STAR
    ↓
OBJECTIVES
    ↓
PRINCIPLES
    ↓
RULES
    ↓
SKILLS
    ↓
AGENTS
    ↓
ORCHESTRATION
    ↓
EXECUTION
    ↓
EVIDENCE
    ↓
MEASUREMENT
    ↓
EVOLUTION
```

## 7. Relación entre Principles y Rules

F0-S3 no escribe las Rules de la Factory. La transformación posterior
será:

```text
Principio
↓
Interpretación operativa
↓
Rule
↓
Validación
↓
Aplicación
```

Ejemplos conceptuales (ilustran la relación; las Rules definitivas
corresponden a F1):

```text
P03 — Evidencia antes de avanzar
        ↓
F1 Rule
"Un Sprint no puede pasar a Completed
sin evidencia de validación."
```

```text
P09 — Least Privilege
        ↓
F1 / F3 Rule
"Un Agent solamente puede utilizar las
herramientas necesarias para su responsabilidad."
```

## 8. Gestión de conflictos

Los principios no son reglas absolutas aisladas; cuando entran en
conflicto, la decisión considera riesgo, impacto, reversibilidad,
evidencia, necesidad, alcance y autorización. Conflictos típicos:

```text
Automatización
↕
Control humano
```

```text
Velocidad
↕
Validación
```

```text
Autonomía
↕
Seguridad
```

Las reglas operativas de F1 establecerán cómo resolver estos casos de
manera consistente.

## 9. Priorización conceptual

Cuando no sea posible maximizar simultáneamente todos los objetivos, la
Factory preservará en este orden:

```text
1. Seguridad y control
2. Integridad del sistema
3. Calidad y verificabilidad
4. Trazabilidad
5. Recuperabilidad
6. Productividad
7. Velocidad
```

Esta jerarquía no resta importancia a productividad o velocidad: significa
que una ganancia de velocidad no justifica automáticamente una degradación
significativa de seguridad, integridad, calidad o control.

## 10. Principios no negociables

Base especialmente crítica; su traducción operativa y mecanismo de
cumplimiento corresponden principalmente a F1:

- **P01 — Máxima autonomía dentro de límites conocidos**
- **P02 — Control humano de decisiones críticas**
- **P03 — Evidencia antes de avanzar**
- **P05 — No arreglar una cosa rompiendo otra**
- **P06 — No inventar requisitos**
- **P09 — Least Privilege**
- **P13 — Trazabilidad de extremo a extremo**
- **P14 — Fallar de forma segura**
- **P23 — Seguridad por diseño**
- **P25 — Medir antes de afirmar mejora**
- **P26 — Autonomía ganada mediante evidencia**

## 11. Relación con F0-S4

Estos principios proporcionan restricciones y criterios conceptuales para
la arquitectura de la Factory. F0-S4 responderá:

> **¿Cómo debe organizarse el sistema para respetar los principios definidos?**

```text
F0-S1
Identidad y límites
        ↓
F0-S2
Dirección y objetivos
        ↓
F0-S3
Principios y criterios
        ↓
F0-S4
Arquitectura conceptual
```

F0-S3 no define componentes arquitectónicos concretos.

## 12. Evolución de principios

Los principios son relativamente estables, pero no inmutables. Una
modificación significativa considerará evidencia, experiencia acumulada,
resultados observados, cambios de alcance, cambios arquitectónicos, nuevos
riesgos, nuevas necesidades e impacto sobre Rules y componentes
existentes. Una evolución importante quedará documentada y versionada. Los
principios no deberán cambiar únicamente para justificar retrospectivamente
una implementación existente.
