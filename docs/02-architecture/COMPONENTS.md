# COMPONENTS — AI Software Factory — F0-S4 Componentes arquitectónicos

Fase: F0 — Fundaciones.
Sprint: F0-S4 — Arquitectura conceptual.
Estado: diseño conceptual. No implementa la Factory.

Cada componente documenta identificador, nombre, propósito,
responsabilidad, entradas conceptuales, salidas conceptuales, relaciones,
límites y dependencia con fases futuras. Las fichas son posiciones
arquitectónicas, no especificaciones de implementación: ningún componente
existe todavía como software.

Documento base: `SYSTEM-OVERVIEW.md` (visión, relaciones, flujo).
Diagrama: `ai-software-factory-architecture.mmd`.

## C01 — Human

- Propósito: ejercer la autoridad final sobre objetivos, prioridades,
  arquitectura, permisos, criterios de aceptación, riesgos, excepciones,
  decisiones críticas y evolución de la Factory.
- Responsabilidad: definir y priorizar el trabajo; autorizar delegación y
  autonomía; aprobar o rechazar avances en los Human Gates; decidir ante
  excepciones.
- Entradas conceptuales: objetivos, necesidades, evidencia presentada por
  el sistema, propuestas de evolución.
- Salidas conceptuales: Tasks definidas, criterios de aceptación,
  autorizaciones, decisiones, aprobaciones.
- Relaciones: origina Task (C02); autoriza Rules (C03); resuelve los
  Human Gates del Orchestrator (C04); aprueba Evolution (C15).
- Límites: no ejecuta directamente el trabajo delegado; no opera fuera de
  los límites que él mismo aprobó sin revisarlos primero. El objetivo es
  eliminar intervención en lo seguro y verificable, no eliminar al
  desarrollador (P02).
- Fases futuras: F0-S7 precisará la gobernanza y decisiones; F1
  traducirá su autoridad en Rules; todas las fases lo mantienen como
  autoridad final.

## C02 — Task

- Propósito: representar el trabajo como unidad explícita, priorizable,
  ejecutable, validable y trazable.
- Responsabilidad: portar objetivo, alcance, criterios de aceptación,
  prioridad y estado; vincular todo lo que derive de ella.
- Entradas conceptuales: objetivos y prioridades del Human (C01).
- Salidas conceptuales: unidad de trabajo definida con criterios de
  aceptación.
- Relaciones: deriva del Human; se ejecuta bajo Rules (C03); la coordina
  el Orchestrator (C04); todo (plan, cambio, commit, test, review, PR,
  CI, merge, release, deploy) se traza contra ella (C12).
- Límites: no contiene lógica de ejecución ni de producto; no crea
  objetivos por sí misma. Las necesidades de un Product nunca redefinen
  qué es una Task (P29, riesgo R08).
- Fases futuras: F0-S5 diseñará su ciclo de vida y estados; F1 definirá
  las Rules que la gobiernan.

## C03 — Rules

- Propósito: establecer los límites y criterios operativos que hacen
  legítima cualquier delegación.
- Responsabilidad: acotar permisos, autonomía, validación exigida y
  condiciones de avance; derivar de los principios (F0-S3) reglas
  concretas y validables.
- Entradas conceptuales: principios (P01–P30), objetivos (F0-S2),
  decisiones humanas.
- Salidas conceptuales: límites aplicables a cada tarea y componente.
- Relaciones: autorizadas por el Human (C01); acotan la Task (C02) y al
  Orchestrator (C04); su cumplimiento se verifica en Validation (C10);
  evolucionan vía Evolution (C15).
- Límites: F0-S4 no escribe Rules operativas; solo reserva su posición.
  Ninguna Rule amplía por sí misma la autoridad de quien la ejecuta
  (capability ≠ authority).
- Fases futuras: F1 diseña e implementa las Rules; F0-S7 y F3/F6/F9 las
  desarrollan en sus ámbitos.

## C04 — Orchestrator

- Propósito: coordinar tareas, estados, agentes, contexto, validaciones,
  recuperación y Human Gates.
- Responsabilidad: planificar, asignar, secuenciar, supervisar el avance
  y escalar al humano. Solo coordina dentro de las Rules.
- Entradas conceptuales: Tasks (C02), Rules aplicables (C03), estado y
  evidencia de las ejecuciones.
- Salidas conceptuales: asignaciones, secuenciación, decisiones de
  avance, detención o escalado.
- Relaciones: recibe de Rules sus límites; asigna a Agents (C05);
  provee Context (C06); atraviesa Human Gates (C01); dirige hacia
  Validation (C10); activa Recovery (C13).
- Límites: coordina, no sustituye responsabilidades; no contiene la
  lógica de los componentes especializados ni la del producto (P11;
  riesgos R03, R04). F0-S4 no define arquitectura concreta de
  orquestación ni Orchestrator funcional.
- Fases futuras: fases de orquestación y automatización lo diseñarán;
  F0-S5 definirá cómo fluye el trabajo a través de él.

## C05 — Agents

- Propósito: asumir responsabilidades ejecutoras acotadas y separadas
  dentro de los límites delegados.
- Responsabilidad: ejecutar el trabajo asignado mediante Skills (C07) y
  Tools (C08); producir resultados verificables; detenerse y escalar ante
  ambigüedad o falta de evidencia.
- Entradas conceptuales: asignación del Orchestrator (C04), contexto
  mínimo necesario (C06), Rules aplicables (C03).
- Salidas conceptuales: resultados de ejecución con evidencia asociada.
- Relaciones: ejecutan bajo el Orchestrator; usan Skills y Tools;
  producen en Execution (C09); nunca declaran su propio éxito (eso es de
  Validation, C10; P10).
- Límites: sin acceso ilimitado; solo permisos necesarios (P09). Nunca
  un Agent monolítico con todas las responsabilidades (riesgo R04). No
  existen como implementación en F0-S4.
- Fases futuras: F2/F3 diseñarán sus responsabilidades y permisos
  concretos.

## C06 — Context / Knowledge

- Propósito: proveer a cada ejecutor la información necesaria y conservar
  el conocimiento validado del sistema.
- Responsabilidad: seleccionar el contexto relevante (disponible →
  relevante → necesario, P12); versionar el conocimiento crítico en
  artefactos (P18, P19); minimizar datos sensibles (P24).
- Entradas conceptuales: contexto disponible, decisiones, evidencia y
  lecciones de ejecuciones.
- Salidas conceptuales: contexto mínimo necesario por asignación;
  conocimiento versionado reutilizable.
- Relaciones: alimenta a Agents (C05) vía el Orchestrator (C04);
  recibe evidencia (C11); su evolución se gobierna por Evolution (C15).
- Límites: más contexto no implica automáticamente mejores resultados;
  el contexto excesivo degrada precisión, costo, velocidad, seguridad y
  mantenibilidad (riesgo R07). Nada fuera de lo necesario se registra o
  transmite.
- Fases futuras: F0-S6 (herramientas y entorno) y F3 precisarán su
  gestión; Git será pieza de su versionado.

## C07 — Skills

- Propósito: conservar procedimientos reutilizables validados para no
  reinventarlos en cada ejecución.
- Responsabilidad: encapsular un procedimiento con sus precondiciones,
  pasos, validación esperada y límites; solo existen las justificadas por
  evidencia (P07, P08).
- Entradas conceptuales: conocimiento validado (C06), propuestas de
  Evolution (C15).
- Salidas conceptuales: procedimientos invocables por Agents (C05).
- Relaciones: usadas por Agents; creadas o modificadas solo vía
  Evolution con aprobación humana; su uso se traza (C12).
- Límites: no todo procedimiento debe convertirse en Skill; una Skill no
  sustituye el criterio del Agent ni la validación del resultado. F0-S4
  no crea Skills.
- Fases futuras: fases de capacidades las diseñarán; F11 evaluará cuáles
  conservan valor.

## C08 — Tools

- Propósito: proporcionar capacidades técnicas concretas para ejecutar el
  trabajo.
- Responsabilidad: ejecutar operaciones acotadas (p. ej. testing,
  revisión, documentación, medición en el futuro) sin definir objetivos
  ni autorizar acciones.
- Entradas conceptuales: invocación de un Agent (C05) vía una Skill
  (C07), dentro de permisos.
- Salidas conceptuales: resultados técnicos y registros de operación.
- Relaciones: sirven a Agents; operan dentro de Execution (C09); están
  al servicio del sistema, nunca al revés (P21): son reemplazables.
- Límites: ninguna herramienta define la arquitectura ni autoriza por sí
  misma; OpenCode, GitHub, modelos e integraciones son entorno actual,
  no premisas arquitectónicas. Sin infraestructura innecesaria (P22).
- Fases futuras: F0-S6 precisará herramientas y entorno; cada fase
  elegirá las suyas por capacidad necesaria.

## C09 — Execution

- Propósito: acotar dónde y bajo qué condiciones ocurre el trabajo
  delegado.
- Responsabilidad: delimitar permisos, recursos y reversibilidad de cada
  ejecución; garantizar que lo ejecutado sea observable.
- Entradas conceptuales: asignación (C04), permisos delegados (C03),
  invocaciones de Tools (C08).
- Salidas conceptuales: resultados observables con registros de
  operación.
- Relaciones: precede obligatoriamente a Validation (C10); ante fallo,
  activa Recovery (C13).
- Límites: ejecución ≠ éxito; continuar ciegamente ante un fallo está
  prohibido (P14). F0-S4 no implementa ejecución ni automatizaciones.
- Fases futuras: el diseño del flujo (F0-S5) y las fases de ejecución
  la concretarán.

## C10 — Validation

- Propósito: contrastar cada resultado contra los criterios de aceptación
  humanos antes de permitir su avance.
- Responsabilidad: aplicar tests, revisiones, verificaciones y criterios;
  declarar avance o rechazo con evidencia.
- Entradas conceptuales: resultados de Execution (C09), criterios de la
  Task (C02), Rules aplicables (C03).
- Salidas conceptuales: veredicto de avance con evidencia asociada.
- Relaciones: separa Execution de Evidence (C11); alimenta Recovery
  (C13) ante rechazo; es ejercida por responsabilidades distintas de
  quien implementó (P10: Testing ≠ declaración de éxito).
- Límites: nada avanza sin validación (P03); la validación no negocia
  los criterios, los aplica. Su ausencia invalida cualquier afirmación
  de éxito (riesgo R06).
- Fases futuras: F0-S5 situará sus puertas; F1 y fases de calidad la
  implementarán.

## C11 — Evidence

- Propósito: producir la prueba verificable de lo ejecutado y validado.
- Responsabilidad: conservar tests, revisiones, artefactos, logs,
  resultados de CI, verificaciones y evidencia de ejecución vinculadas a
  su origen.
- Entradas conceptuales: resultados validados (C10), registros de
  Execution (C09).
- Salidas conceptuales: paquetes de evidencia vinculados a la Task.
- Relaciones: alimenta Traceability (C12) y Measurement (C14); sostiene
  Recovery (C13) con material de diagnóstico.
- Límites: la declaración de un modelo o herramienta nunca es evidencia
  por sí misma; sin evidencia no hay avance, autonomía ni mejora
  afirmable (P03, P25, P26).
- Fases futuras: fases de validación y medición definirán sus formatos;
  F11 la consumirá.

## C12 — Traceability

- Propósito: relacionar cada actividad relevante con su origen,
  ejecución, validación y resultado, de extremo a extremo.
- Responsabilidad: mantener la cadena objetivo → trabajo → plan →
  cambio → commit → test → review → PR → CI → merge → release → deploy
  (P13) como parte de la arquitectura, no como agregado final.
- Entradas conceptuales: Tasks (C02), evidencia (C11), registros de
  cada etapa.
- Salidas conceptuales: traza auditable por unidad de trabajo.
- Relaciones: consume Evidence; posibilita Measurement (C14) y
  Recovery (C13); permite al Human auditar cualquier decisión.
- Límites: trazar no es registrarlo todo indiscriminadamente (P24);
  es vincular lo relevante a su origen y autorización.
- Fases futuras: F0-S5 la integrará en el flujo; Git será pieza
  fundamental (P19).

## C13 — Recovery

- Propósito: devolver al sistema a un estado conocido y válido ante
  errores, excepciones o degradación.
- Responsabilidad: detectar, detener o aislar, preservar evidencia,
  diagnosticar y recuperar o escalar (P14); comprender la causa antes de
  repetir (P15: FAIL → DIAGNOSE → SAFE RETRY? → RETRY / RECOVER–ESCALATE).
- Entradas conceptuales: fallos y señales de cualquier etapa, evidencia
  disponible (C11), estado anterior.
- Salidas conceptuales: sistema recuperado o escalado al humano con
  diagnóstico.
- Relaciones: transversal a todas las etapas; precede a cualquier
  reintento; informa a Evolution (C15) para prevenir recurrencia.
- Límites: nunca repetir ciegamente una operación problemática; la
  idempotencia (P16) y la reversibilidad (P17) se diseñan donde sea
  viable, con excepciones explícitas.
- Fases futuras: F0-S5 diseñará sus transiciones; fases de ejecución y
  operación la implementarán.

## C14 — Measurement

- Propósito: comparar objetivamente para poder afirmar mejora.
- Responsabilidad: contrastar baseline → cambio → medición →
  comparación → conclusión basada en evidencia (P25); custodiar la
  hipótesis aspiracional 20×–30× con sus indicadores acompañantes
  (calidad, trazabilidad, errores, rework, intervención, recuperación).
- Entradas conceptuales: trazas (C12) y evidencia (C11) sobre trabajo
  comparable.
- Salidas conceptuales: conclusiones de mejora o su refutación.
- Relaciones: consume Traceability; alimenta Evolution (C15); responde
  a la North Star sin anticipar sus resultados.
- Límites: F0-S4 la concibe como capacidad sin implementar F11, sin
  métricas definitivas y sin afirmar mejora alguna actual. Medir es
  comparar, no celebrar velocidad (P04).
- Fases futuras: F10 aportará la primera evidencia formal (piloto);
  F11 consolidará medición y evolución.

## C15 — Evolution

- Propósito: cambiar el sistema (Rules, Skills, Agents, arquitectura) de
  forma versionada y solo con evidencia suficiente y aprobación humana.
- Responsabilidad: proponer, justificar (necesidad, evidencia,
  limitación, riesgo, costo, beneficio, mantenibilidad, impacto — P20),
  versionar (qué, cuándo, por qué, impacto, evidencia — P19) y someter a
  aprobación cada cambio del sistema.
- Entradas conceptuales: mediciones (C14), evidencia acumulada (C11),
  experiencia y nuevos riesgos.
- Salidas conceptuales: cambios versionados de Rules (C03), Skills
  (C07), Agents (C05) o arquitectura.
- Relaciones: actualiza los instrumentos; nunca se auto-aplica sin el
  Human (C01); nunca justifica retrospectivamente lo implementado.
- Límites: la arquitectura evoluciona cuando el sistema lo necesita, no
  por moda tecnológica (P20); la complejidad nueva se justifica por
  necesidad real (P27) y sin exigir reconstrucción completa (P28).
- Fases futuras: F11 la operará en régimen; F0-S7 gobernará sus
  decisiones.

## Decisiones arquitectónicas importantes y su principio

| Decisión | Principios |
|----------|-----------|
| Cadena supervisada Human → Task → Rules → Orchestrator | P01, P02, P09 |
| Coordinación sin sustitución de responsabilidades | P10, P11, P27 |
| Nada avanza sin Validation ni Evidence | P03, P06 |
| Trazabilidad estructural, no agregada al final | P13, P19 |
| Recovery transversal con diagnóstico previo al reintento | P14, P15, P16, P17 |
| Contexto mínimo y minimización de datos | P12, P24 |
| Measurement y Evolution como capacidades sin implementar F11 | P20, P25, P26, P30 |
| Independencia tecnológica y local-first | P21, P22 |
| Frontera Factory / Product | P29 |
| Seguridad desde el diseño | P23, P09 |
| Calidad junto a velocidad, nunca a su costa | P04, P05 |
| Reutilizar y automatizar solo con valor justificado | P07, P08 |
| Diseñar para evolución versionada | P18, P19, P28 |
