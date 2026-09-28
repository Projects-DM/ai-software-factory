# RULE-CONTRACT — F1-S1 Contrato formal de Rules

Fase: F1 — Rules. Sprint: F1-S1 — Taxonomía y contrato.
Estado: contrato CONCEPTUAL y documental. No implementa enforcement,
automatización ni integración con herramientas.

Este documento define qué es una Rule válida y qué estructura debe
tener. Quien cree una Rule (F1-S2…) la instancia campo por campo sin
reinventar semántica. Base: AGENTS.md, MASTER-PLAN.md, F0-S1…F0-S7.

## 1. Definición formal de Rule

Una Rule es una **norma operativa versionada, con autoridad explícita,
que establece qué debe ocurrir (o está prohibido) cuando se cumplen
unas condiciones dentro de un alcance definido, y qué evidencia debe
producirse**. Una Rule solo obliga cuando está en estado ACTIVE, con
campos obligatorios completos y aprobación registrada.

Un artefacto es una Rule válida si y solo si: identifica ID/versión/
estado; declara obligatoriedad normativa; define alcance y condiciones;
exige acción o restricción; designa autoridad; especifica evidencia; y
recorrió su lifecycle con aprobación. Sin estos elementos es texto
orientativo, no Rule.

Distinciones:

| Artefacto | Qué es | Qué no es (vs Rule) |
|-----------|--------|---------------------|
| Principle | Orientación estable para decidir (P01–P30) | No exigible por sí mismo; no versiona conducta |
| Policy | Postura general de la Factory | Sin condición/acción/evidencia estructuradas |
| Procedure | Secuencia de pasos (cómo hacer) | Describe, no obliga; corresponde a Skill futura |
| Skill | Procedimiento reutilizable validado (F2) | Capacidad, no norma |
| Agent | Responsabilidad ejecutora (F3) | Ejecuta bajo Rules, no es norma |
| Tool | Capacidad técnica (C08) | `Tool ≠ Authority`; no obliga |
| Permission | Autorización puntual | Deriva de Rules/autoridad; no es norma general |
| Evidence | Prueba de lo ocurrido | Demuestra, no prescribe |
| Decision | Determinación autorizada (ADR/gate) | Resuelve un caso; la Rule rige clases de casos |

Rige `CAPABILITY ≠ AUTHORIZATION`: la autorización exige PERMISO
EXPLÍCITO + ALCANCE DEFINIDO + CONDICIONES SATISFECHAS + EVIDENCIA.
Ningún campo del contrato permite que la capacidad implique permiso.

## 2. Análisis de la estructura inicial

Estructura propuesta evaluada (17 campos): ID, Nombre, Propósito,
Alcance, Categoría, Obligatoriedad, Severidad, Condición, Acción
requerida, Restricción, Excepción, Evidencia, Autoridad, Dependencias,
Versión, Estado, Fecha.

- Se conservan 16 campos (todos salvo Fecha).
- Se elimina `Fecha` como campo aislado: ambiguo (¿creación,
  aprobación o vigencia?). Se sustituye por fechas explícitas en
  Estado (propuesta, aprobación, entrada en vigor, desactivación) e
  Historial. Misma información, sin ambigüedad.
- Se agregan 4 campos exigidos por el alcance F1-S1 sin equivalente
  previo: Precedencia (§14), Relación general/específica (§17),
  Revisión (criterios F0-S7 §21) e Historial (cadena supersedes F0-S7).
- Excepción y Evidencia pasan de texto libre a sub-bloques
  estructurados (§§13, 22 de F1-S1).

## 3. Contrato definitivo (por campo)

Formato por campo: nombre — propósito — obligatoriedad — contenido —
uso/restricciones — relaciones.

1. **ID** — identificador único estable (`R-<CAT>-<NNN>`, p. ej.
   `R-SEC-001`). Obligatorio. Inmutable tras aprobación; el cambio
   crea nueva versión, no nuevo ID. Relaciona citas, dependencias y
   traza.
2. **Nombre** — título breve y descriptivo. Obligatorio. Sin jerga de
   producto; `Factory ≠ Product`.
3. **Propósito** — problema que resuelve y valor verificable (P08).
   Obligatorio. Cita principios F0-S3 que desarrolla.
4. **Alcance** — dónde aplica: Factory/fase/workflow/tipo de tarea/
   agente/Skill/herramienta/repositorio/entorno/tipo de acción.
   Obligatorio. Modelo conceptual; sin mecanismos técnicos de
   imposición (F1-S1 no los diseña). Sin alcance no hay aplicabilidad.
5. **Categoría** — una de las 11 de `RULE-TAXONOMY.md` (`RC-01…RC-11`).
   Obligatorio. Determina el sprint F1-S2…F1-S12 que la desarrolla.
6. **Obligatoriedad** — `MUST / MUST NOT / SHOULD / MAY / HUMAN
   APPROVAL` (sección 4). Obligatorio. Fija fuerza normativa.
7. **Severidad** — `CRITICAL / HIGH / MEDIUM / LOW` (sección 5).
   Obligatorio. Impacto del incumplimiento; nunca confundir con
   obligatoriedad, prioridad, autoridad, riesgo general ni urgencia.
8. **Condición** — predicado verificable de aplicabilidad (¿cuándo
   aplica?). Obligatorio salvo Rules incondicionales de alcance, que
   lo declaran explícitamente. Distinto de la acción.
9. **Acción requerida** — conducta exigible (¿qué debe ocurrir?).
   Obligatorio si la Rule exige hacer; ausente solo en `MUST NOT`
   puras. Verificable, no aspiracional.
10. **Restricción** — lo prohibido (¿qué está vetado?). Obligatorio en
    `MUST NOT`; opcional como límite adicional en otras. Una Rule
    específica jamás elimina silenciosamente una restricción crítica
    general (§17 F1-S1, en `RULE-GOVERNANCE.md`).
11. **Excepción** — sub-bloque: Rule afectada, Motivo, Condición,
    Alcance, Autoridad, Duración, Riesgo, Evidencia, Revisión.
    Opcional en definición; obligatorio al invocar una excepción.
    Autorizada, acotada en tiempo, revisable, revocable; nunca vía
    informal de ignorar la Rule.
12. **Autoridad** — quién crea/revisa/aprueba/activa/modifica/
    desactiva/depreca y quién autoriza excepciones, derivado de los
    niveles F0-S7 (C01–C06) sin inventar roles: C01–C03 roles
    delegados del ámbito; C04+ autoridad humana designada/final vía
    ADR. Obligatorio. `Capability ≠ Authority` siempre.
13. **Precedencia** — posición frente a colisiones (general vs
    específica; mayor vs menor autoridad; activa vs obsoleta; vigente
    vs anterior). Obligatorio declarar al menos la regla por defecto
    de su categoría. Sin interpretación arbitraria por el agente.
14. **Dependencias** — Rules, principios, ADRs, políticas, contexto o
    artefactos de gobernanza requeridos. Opcional; prohibidas
    dependencias circulares no detectadas (toda dependencia debe
    resolverse a nodos existentes).
15. **Relación** — general/específica: complementa, restringe,
    especializa, reemplaza o entra en conflicto (resuelto por
    precedencia). Opcional; obligatorio si especializa otra Rule.
16. **Evidencia** — sub-bloque WHAT/WHEN/WHO/WHY/RESULT/SOURCE +
    momento de producción y responsable. Obligatorio. Debe permitir
    demostrar: Rule activa, aplicabilidad, condiciones conocidas,
    decisión tomada, autoridad y resultado. `Evidence ≠ Validation ≠
    Authorization ≠ Decision`.
17. **Versión** — semántica documental (`vMAYOR.menor`): MAYOR ante
    cambio normativo, menor ante aclaración. Obligatorio. Registra
    qué cambió, quién aprobó, cuándo entró en vigor, qué sustituyó y
    compatibilidad. Ningún cambio relevante es edición silenciosa.
18. **Estado** — lifecycle `RULE-LIFECYCLE` (PROPOSED→UNDER
    REVIEW→APPROVED→ACTIVE→SUPERSEDED/DEPRECATED) con fechas de
    propuesta, aprobación, entrada en vigor y desactivación.
    Obligatorio. Debe poderse determinar qué Rule estaba activa en un
    momento T.
19. **Revisión** — criterios y triggers de reevaluación (Keep / Modify
    / Supersede / Deprecate, F0-S7 §21). Obligatorio.
20. **Historial** — cadena de sustituciones (`R-XXX v2 supersedes
    v1`), preservada y trazable. Obligatorio desde v2.

## 4. Obligatoriedad

- **MUST** — exigible siempre que aplica. Incumplimiento = violación
  (bloqueo/escalado según severidad). Excepción solo con autoridad
  C04+ y evidencia. 
- **MUST NOT** — prohibición absoluta en su alcance. Violación =
  STOP + evidencia + escalado. Excepción solo temporal, C05+, con
  revisión fechada.
- **SHOULD** — conducta esperada; desviarse exige justificación
  registrada con evidencia. Diferencia con MUST: MUST no admite
  desviación por criterio del ejecutor; SHOULD admite desviación
  motivada y trazada, nunca silenciosa.
- **MAY** — permitido, no exigido; sin evidencia de cumplimiento
  obligatoria, con traza de uso.
- **HUMAN APPROVAL** — el avance exige decisión humana explícita
  (Human Gate F0-S5). Representación: campo Obligatoriedad =
  `HUMAN APPROVAL` + Autoridad = decisor humano competente +
  Evidencia de aprobación vinculada. Sin aprobación no hay avance.

## 5. Severidad

`CRITICAL` (compromete seguridad/integridad/control) > `HIGH`
(degrada calidad/trazabilidad/recuperación) > `MEDIUM` (fricción o
retrabajo acotado) > `LOW` (mejora menor). La severidad mide impacto
del incumplimiento y no equivale a obligatoriedad (un SHOULD puede ser
CRITICAL), prioridad de implementación, autoridad competente, riesgo
general del sistema ni urgencia temporal.

## 6. Alcance, condiciones y comportamiento

- Alcance: las 10 dimensiones de la ficha (campo 4); al menos
  Factory/fase/tipo de acción siempre explícitos.
- `Rule vs Condition vs Action vs Restriction`: la Rule es la norma
  completa; Condition responde ¿cuándo aplica?; Action ¿qué debe
  ocurrir?; Restriction ¿qué está prohibido?; Evidencia ¿qué debe
  producirse? Ningún par se sustituye.
