# HUMAN-GATES — AI Software Factory — F0-S5 Puertas humanas

Fase: F0 — Fundaciones.
Sprint: F0-S5 — Flujo de trabajo.
Estado: diseño conceptual-operativo. No implementa la Factory.

Este documento define conceptualmente qué es un Human Gate y cómo se
relaciona con riesgo, autonomía y escalamiento. Desarrolla las posiciones
lógicas reservadas en F0-S4 (`SYSTEM-OVERVIEW.md`, sección 8) sin crear
la matriz operacional de permisos o políticas, que corresponde a F1.

## 1. Definición

Un Human Gate es un punto de decisión/autorización dentro del
lifecycle, donde el avance requiere una decisión humana explícita y
registrada antes de continuar.

> **Human Gate no es un estado del lifecycle.**

No es una pausa informal ni una supervisión pasiva: es una transición
bloqueada hasta que el humano (o un rol con autoridad expresamente
delegada para ese tipo de decisión) autoriza, rechaza, modifica o
cancela. La tarea en espera reside en WAITING_HUMAN con estado y
evidencia preservados.

## 2. Propósito

Garantizar que ninguna decisión que requiera criterio, autorización o
conocimiento contextual se tome por omisión, por capacidad técnica o por
velocidad aparente (P02; capability ≠ authority). El objetivo no es
detener el flujo, sino impedir avances ilegítimos: cada puerta existe
para una razón concreta y documentada (riesgo R06: ninguna puerta
ambigua).

## 3. Cuándo puede activarse

Un Human Gate se activa ante:

- riesgo significativo, incertidumbre o ambigüedad no resoluble por
  criterios (P06);
- superación de los límites de autoridad delegada;
- acciones irreversibles o costosas (P17);
- cambios sensibles (permisos, configuración, integraciones, despliegue,
  datos);
- resultados ambiguos o validación no concluyente;
- excepciones, fallos sin vía segura de recuperación;
- cualquier evolución de la propia Factory (Rules, Skills, Agents,
  arquitectura).

## 4. Decisiones que puede detener

- Aprobación del plan y de los criterios de aceptación (PLANNED → READY).
- Asignación y ampliación de permisos o autonomía delegada.
- Avance tras validación fallida o ambigua.
- Integración (CERTIFIED → PR) y despliegue (→ DEPLOYED) cuando el
  riesgo lo exija.
- Reintentos tras agotar el límite diagnosticado.
- Cancelación y evolución del sistema.

No asumir que todas las Tasks requieren todos los Human Gates: la
presencia de cada puerta depende de riesgo, autoridad, incertidumbre,
impacto, irreversibilidad, sensibilidad, resultados ambiguos, fallos sin
recuperación segura y evolución de la propia Factory.

## 5. Relación con el riesgo

A mayor riesgo, irreversibilidad o impacto, mayor exigencia de presencia
humana: el riesgo determina si hay puerta, quién puede abrirla y qué
evidencia exige. El riesgo desconocido se trata como riesgo alto hasta
diagnosticarlo.

## 6. Relación con la autonomía

La puerta es el mecanismo que hace compatible autonomía y control: la
autonomía delegada opera libremente dentro de límites y la puerta la
contiene en sus bordes. Cada nivel de autonomía (modelo conceptual de
F0-S2, sin declarar ningún nivel como alcanzado) redefine dónde están
las puertas, nunca si existen:

### Nivel 1 — Assistance

```text
Human
↓
Task
↓
AI assistance
↓
Human executes
```

El humano ejecuta; la IA asiste. La puerta es permanente: cada acción
relevante la decide el humano.

### Nivel 2 — Supervised execution

```text
Human
↓
Task
↓
Factory executes
↓
Human supervises
```

La Factory ejecuta bajo supervisión directa; el humano observa con
capacidad de detener, aprobar o corregir en cada paso significativo.

### Nivel 3 — Controlled autonomy

```text
Human
↓
Task
↓
Factory executes within limits
↓
Human Gate when required
```

Ejecución autónoma dentro de límites con puertas en los puntos definidos
(riesgo, irreversibilidad, ambigüedad, evolución). Dentro de los límites
el flujo avanza; en los bordes se detiene.

### Nivel 4 — Conditioned autonomy

```text
Task
↓
Factory
↓
Automatic execution
↓
Automatic validation
↓
Exception → Human
```

Ejecución y validación automáticas bajo condiciones estrictas y
validadas; cualquier excepción, ambigüedad o desviación escala al humano.
Es el nivel más exigente en evidencia previa, no el más permisivo: solo
existe donde la confiabilidad está demostrada (P26).

Estos niveles son un modelo conceptual, no capacidades actualmente
implementadas.

## 7. Escalamiento

Escalar es transferir al humano una decisión con su contexto: qué
ocurrió, qué evidencia existe, qué opciones hay, qué recomienda el
sistema y qué riesgo conlleva cada opción. Todo escalado deja la tarea
en WAITING_HUMAN; ningún escalado se resuelve por silencio o por
repetición. Ante excepción sin vía segura, escalar es la única transición
válida. La decisión humana puede reactivar la tarea en el estado
apropiado según el estado de origen, la decisión tomada, la condición
que originó la espera, la evidencia disponible y las reglas aplicables;
WAITING_HUMAN no tiene como únicas salidas READY o PLANNED.

## 8. Autorización

Solo autoriza quien tenga autoridad para ese tipo de decisión: el Human
por defecto; un rol designado únicamente dentro de la delegación
expresa que lo habilita. La autorización queda registrada con quién,
qué, cuándo, sobre qué evidencia y con qué alcance. Autorizar fuera de
la propia autoridad es una contradicción del sistema, no una vía de
avance.

## 9. Resultado de la intervención

Toda intervención humana produce un resultado trazado: aprobar (avance
autorizado), rechazar con observaciones (devolución a ejecución o a
planificación), redirigir (cambio de plan o alcance), cancelar (paso a
CANCELLED con motivo) o solicitar más evidencia (permanencia en
WAITING_HUMAN). La intervención sin registro equivale a no haber
intervenido: lo no trazado no cuenta como control.
