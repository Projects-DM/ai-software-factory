# GOVERNANCE — AI Software Factory — F0-S7 Gobernanza y decisiones

Fase: F0 — Fundaciones.
Sprint: F0-S7 — Gobernanza y decisiones.
Estado del modelo: CONCEPTUAL. No implementado.

Este documento define quién puede decidir qué, bajo qué condiciones,
con qué evidencia y cómo queda registrada esa decisión. Es el modelo de
gobernanza de la Factory: autoridad, niveles de decisión, escalamiento,
excepciones, autonomía, revisión, trazabilidad y evolución.

No implementa reglas, permisos, automatizaciones ni mecanismos
operativos: eso pertenece a fases posteriores. Las decisiones aquí
descritas se toman hoy de forma humana y directa; el modelo prepara su
gobernanza futura sin anticiparla.

Documentos relacionados: `ADR-INDEX.md`, `ADR-TEMPLATE.md`,
`CHANGE-GOVERNANCE.md` (este directorio), `governance-flow.mmd`
(diagrama). Base: `docs/01-foundations/` (F0-S1–S3),
`docs/02-architecture/` (F0-S4), `docs/03-workflow/` (F0-S5),
`docs/04-tools/` (F0-S6).

## 1. Definición

Gobernanza es el sistema por el cual la Factory decide, autoriza,
registra, revisa y evoluciona sus decisiones. Responde cuatro preguntas
para cada decisión relevante: quién (autoridad), bajo qué condiciones
(límites y riesgo), con qué evidencia (justificación comprobable) y cómo
queda registrada (traza persistente y versionada).

## 2. Principios de gobernanza

- Solo la autoridad correspondiente decide; la capacidad técnica nunca
  la sustituye (`Capability ≠ Authority`; P09).
- Ninguna preferencia aislada (`Preference → Decision`) basta para
  decisiones relevantes: se exige el modelo completo de la sección 3.
- Lo crítico permanece bajo control humano (P02); la autonomía se gana
  con evidencia (P26).
- Nada se modifica silenciosamente: principios, arquitectura y reglas
  cambian solo por decisión trazada (P13, P19, P23).
- Ante conflicto irresoluble con la autoridad disponible: STOP →
  ESCALATE; nunca inventar una solución (P06).

## 3. Modelo de decisión

```text
Context
↓
Problem
↓
Options
↓
Criteria
↓
Evidence
↓
Decision
↓
Consequences
↓
Review
```

Cada decisión relevante recorre estas etapas con registro: contexto que
la motiva, problema que resuelve, opciones consideradas, criterios de
evaluación, evidencia que la sostiene, decisión adoptada, consecuencias
asumidas y revisión posterior. Omitir etapas solo es legítimo para
decisiones triviales (C01, ver `CHANGE-GOVERNANCE.md`).

## 4. Autoridad y niveles de decisión

La autoridad depende del impacto, no del rol técnico de quien propone.
Niveles conceptuales (sin matriz automática de permisos, que pertenece
a fases posteriores):

```text
C01 Trivial → quien ejecuta, con registro mínimo
C02 Operativo → rol responsable del ámbito, con evidencia
C03 Técnico → responsable técnico + revisión
C04 Arquitectónico → ADR + aprobación humana
C05 Estratégico → autoridad humana designada
C06 Fundacional → autoridad humana final + revisión de impacto sistémico
```

Regla de riesgo/autoridad:

```text
Low risk → automatic (dentro de límites validados)
Known / bounded → autonomous within limits
Higher risk → human gate
Unknown / critical → human decision
```

Gobernanza no es cuello de botella: lo conocido y acotado fluye; solo lo
riesgoso, desconocido o crítico exige puerta o decisión humana. Estos
niveles son conceptuales en F0; no existen mecanismos automáticos de
autorización.

## 5. Propuesta vs decisión

```text
AI MAY PROPOSE
≠
AI MAY DECIDE
```

Un Agent puede conceptualmente investigar, comparar, presentar
alternativas, identificar riesgos y elaborar una recomendación técnica.
La autoridad final depende del nivel de decisión y de las reglas
aplicables. Cuando el nivel requiera decisión humana, rige `AI proposes
≠ Human decides`: proponer no es decidir, recomendar no es autorizar.

## 6. Escalamiento

```text
Agent
↓
Cannot decide safely
↓
Escalate
↓
Reviewer / Human
↓
Decision
↓
Continue / Modify / Stop
```

Regla fundamental: un Agent no debe compensar la falta de autoridad
inventando una decisión (P06). Escalar transfiere la decisión con su
contexto (qué ocurrió, evidencia, opciones, riesgos); la Task espera en
WAITING_HUMAN; el resultado (continuar, modificar, detener) queda
registrado.

## 7. Excepciones

Excepción = desviación temporal y autorizada respecto de una regla,
principio operativo o procedimiento establecido:

```text
Exception
↓
Reason
↓
Risk
↓
Scope
↓
Authorization
↓
Duration
↓
Evidence
↓
Review
```

Una excepción nunca se convierte automáticamente en regla. Si las
excepciones se vuelven permanentes o recurrentes, se revisa el sistema
que las originó (posible cambio gobernado, no acomodación silenciosa).
Detalle operativo en `CHANGE-GOVERNANCE.md`.

## 8. Conflictos

Conflictos posibles entre Rules, Principles, Architecture, Product
requirements, Tool limitations, Agent instructions y Human decisions. La
prioridad conceptual (F0-S3 §9) se preserva:

```text
Fundamental constraints
↓
Security / Control
↓
System Integrity
↓
Quality / Verification
↓
Traceability
↓
Recovery
↓
Productivity
↓
Speed
```

Si el conflicto no puede resolverse dentro de la autoridad disponible:
STOP → ESCALATE. No inventar una solución. Las necesidades de un
Product no modifican unilateralmente los principios, límites ni la
arquitectura de la Factory. Cualquier cambio de la Factory debe seguir
su propio modelo de gobernanza. Un Product tiene su propia arquitectura
y evoluciona independientemente (P29).

```text
Factory ≠ Product
```

## 9. Autonomía gobernada

```text
Known responsibility
+
Known limits
+
Known tools
+
Known validation
+
Known recovery
↓
Authorized autonomy
```

Y se rechaza conceptualmente:

```text
Capability
↓
Unlimited authority
```

Distinciones obligatorias: Capability (puede hacerlo) ≠ Authority
(está facultado) ≠ Responsibility (le corresponde) ≠ Authorization
(se le permitió en este caso). La capacidad técnica no es permiso para
actuar. El nivel efectivo de autonomía por tipo de tarea se determina
con evidencia (P26), no por declaración.

## 10. Control humano

El humano conserva objetivos, prioridades, arquitectura, permisos
sensibles, criterios de aceptación, riesgos, excepciones, decisiones
críticas y evolución de la propia Factory (F0-S1). Los principios
fundacionales (F0-S3) no pueden ser modificados silenciosamente por un
Agent; para cambios relevantes sobre principios:

```text
Principle
↓
Proposal
↓
Impact Analysis
↓
Human Review
↓
Decision
↓
Documentation
↓
Validation
```

Conecta con P02 (control humano), P06 (no inventar), P09 (mínimo
privilegio), P13 (trazabilidad), P23 (seguridad por diseño) y P26
(autonomía con evidencia).

## 11. Estados de decisión

```text
PROPOSED
UNDER REVIEW
ACCEPTED
IMPLEMENTED
VALIDATED
REJECTED
SUPERSEDED
DEPRECATED
```

Relaciones preservadas: `PROPOSED → REJECTED`; `ACCEPTED → SUPERSEDED`;
`ACCEPTED → DEPRECATED`. Y las desigualdades estructurales:

```text
ACCEPTED ≠ IMPLEMENTED
IMPLEMENTED ≠ VALIDATED
```

Aceptar no es implementar; implementar no es validar. El historial nunca
se borra: `ADR-001 → ADR-007 supersedes ADR-001 → ADR-014 supersedes
ADR-007`; cada supersesión conserva qué cambió, por qué y con qué
evidencia (detalle en `ADR-INDEX.md`).

## 12. Trazabilidad de decisiones

```text
Decision ID
↓
Context
↓
Evidence
↓
Decision Maker
↓
Implementation
↓
Validation
↓
Current Status
```

Los cambios relevantes se relacionan con las decisiones que los
autorizan. No se implementa en F0-S7 un sistema de auditoría completo;
la auditoría detallada de ejecuciones corresponde a F8.

## 13. Revisión

```text
Decision
↓
Evidence
↓
Review Trigger
↓
Reassessment
↓
Keep / Modify / Supersede / Deprecate
```

Triggers: cambio de requisitos, nueva evidencia, cambio arquitectónico,
cambio de riesgo, cambio tecnológico, efectos no esperados,
desaparición de la razón original. Revisar no es deshacer por defecto:
mantener una decisión también es un resultado válido cuando la
evidencia la sostiene.

## 14. Conocimiento gobernado

El conocimiento necesario para operar la Factory debe estar
documentado, versionado, localizado, mantenible y trazable. Se evita
depender de memoria personal, conversación aislada, decisiones no
documentadas o configuración local desconocida. Rige: si el
conocimiento es necesario para operar la Factory, debe existir una
representación persistente adecuada (P18, P19).

## 15. Métricas (conceptuales, no implementadas)

Posteriormente podrán medirse: decisiones trazables, decisiones
documentadas, tiempo de resolución, decisiones revertidas, excepciones,
escalaciones, cambios no autorizados, decisiones superseded y
cumplimiento de Human Gates. En F0-S7 no se implementa ninguna métrica;
el detalle corresponde a F8/F11.

## 16. Evolución del modelo

Este modelo es CONCEPTUAL y evoluciona por decisión humana con
evidencia, nunca por auto-modificación de sus ejecutores. Su
implementación (reglas F1, permisos, automatización, auditoría F8)
deberá respetar cada distinción de este documento. Coherencia con
F0-S1–S6: PASS (identidad y límites, North Star y objetivos,
principios, componentes C01–C15, lifecycle y gates, tooling y
separaciones preservadas).
