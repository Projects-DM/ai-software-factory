# F1-S3-RULES-CONTEXT-KNOWLEDGE — Rules de contexto y conocimiento

## 1. Identificación

F1-S3, categoría RC-02 — Context & Knowledge. Serie de IDs `R-CK-NNN`
(CK = serie RC-02, formato `R-<CAT>-<NNN>` del contrato F1-S1). Todas
las Rules: PROPOSED v0.1 — definidas ≠ aprobadas ≠ activas. Sin
enforcement ni sistemas técnicos.

## 2. Propósito

Que cualquier agente futuro opere solo con información NECESARIA +
RELEVANTE + AUTORIZADA + IDENTIFICABLE + VERIFICABLE + VIGENTE +
TRAZABLE, y se detenga o escale cuando sea insuficiente,
contradictoria, ambigua o no confiable.

## 3. Alcance

Los 23 puntos RC-02 del sprint (mínimo necesario → trazabilidad
conceptual). Cubre RF01–RF18.

## 4. Fuera de alcance

Agents, Skills, Orchestrator, permisos/autorización técnica,
seguridad, testing, Git, CI/CD, recovery, autonomía, observabilidad,
certificación, gobernanza general, automatización, infra, piloto,
chatbot, SGC-DM. La trazabilidad aquí es obligación operativa, no
sistema técnico.

## 5. Relación con F0

Desarrolla P03/P06/P09/P12/P13/P18/P19/P20/P25/P26/P29/P30 como
conducta verificable (no los copia). Respeta lifecycle F0-S5, gates
F0-S5, C01–C15 y separaciones F0 (Task≠Issue, Recovery≠Git,
OpenCode≠Tools).

## 6. Relación con F1-S1

Contrato de 20 campos aplicado íntegro; lifecycle, versionado,
precedencia y excepciones según `RULE-GOVERNANCE.md`. Sin contrato
alternativo.

## 7. Relación con F1-S2

Complementa (no duplica): R-GB-002 (no inventar) → R-CK-006/008;
R-GB-003 (alcance) → R-CK-003; R-GB-006 (validación) → R-CK-004/005;
R-GB-008/009 (stop/escalado) → R-CK-007/008; R-GB-010 (evidencia) →
R-CK-009/010. Referenciados como dependencias.

## 8. Definiciones conceptuales

FACT (verificado) ≠ KNOWLEDGE (validado y reutilizable) ≠ CONTEXT
(información de trabajo) ≠ MEMORY (implícita, no registrada) ≠
ASSUMPTION (no verificado, etiquetado) ≠ DECISION (determinación
autorizada) ≠ EVIDENCE (prueba). La memoria implícita y los supuestos
jamás se convierten silenciosamente en hechos.

## 9. Rules RC-02

Precedencia por defecto (todas): especializan la base RC-01 donde
colisionan (igual/mayor autoridad, `RULE-GOVERNANCE.md` §2).
Dependencias comunes: P12/P18/P19, R-GB-002/003/010.
Autoridad de aprobación: humana designada C04 (excepciones C04+,
C05+ temporal para MUST NOT). Esta autoridad rige uniformemente el
campo Autoridad de las 10 Rules (crear/revisar/aprobar/activar/
modificar/desactivar/deprecar); activar/desactivar corresponde a la
autoridad aprobadora o superior. Historial: inicial. Revisión:
triggers F0-S7 §21 salvo indicación.

### R-CK-001 — Contexto mínimo necesario

Propósito: ni insuficiente ni innecesario (P12). Alcance: asignación
y uso de contexto por Task. Obligatoriedad MUST. Severidad HIGH.
Condición: antes de ejecutar cuando sea relevante. Acción: determinar
el contexto mínimo (necesario → relevante → autorizado) y dejar
constancia conceptual vinculada a la Task de qué se consideró, por
qué es necesario y qué límites respeta —obligación, no sistema de
registro: sin formato, herramienta ni almacenamiento definidos aquí—.
Restricción: prohibido operar con contexto insuficiente o cargar
innecesario/no autorizado. Excepción: solo vía mecanismo formal §10
(autoridad mínima C04+). Evidencia: constancia conceptual del
contexto considerado (WHAT/WHEN/WHO/WHY/RESULT/SOURCE).
Versión v0.1. Estado PROPOSED.

### R-CK-002 — Filtro de relevancia

Propósito: solo información relevante justificada. Alcance: toda
información candidata. Obligatoriedad MUST. Severidad MEDIUM.
Condición: al incorporar información al contexto. Acción: evaluar
relevancia contra objetivo/criterios; descartar o justificar la
irrelevante. Restricción: prohibida información irrelevante sin
justificación. Excepción: solo vía mecanismo formal §10 (autoridad
mínima C04+). Evidencia: decisión de
inclusión/exclusión. Versión v0.1. Estado PROPOSED.

### R-CK-003 — Alcance autorizado del contexto

Propósito: contexto dentro de Task + autorización + Rules (P09).
Alcance: toda información utilizada. Obligatoriedad MUST. Severidad
HIGH. Condición: siempre. Acción: verificar pertenencia al alcance
autorizado antes de usar. Restricción: prohibido usar
arbitrariamente información fuera de alcance. Excepción: solo vía
mecanismo formal §10 (autoridad mínima C04+, con redefinición de
Task). Evidencia: verificación de alcance. Versión v0.1.
Estado PROPOSED.

### R-CK-004 — Fuente identificable y confiabilidad

Propósito: origen conocido y confianza proporcional al uso (P03).
Alcance: información empleada en decisiones/ejecución. Obligatoriedad
MUST. Severidad HIGH. Condición: según criticidad del uso e impacto
de la decisión que dependa de la información (sin matriz de riesgo:
la profundidad de evaluación es proporcional a criticidad/impacto).
Acción: identificar fuente; evaluar confiabilidad para el uso
requerido; degradar o rechazar lo no confiable. Restricción:
prohibido decidir sobre fuentes no evaluadas en asuntos críticos.
Excepción: solo vía mecanismo formal §10 (autoridad mínima C04+).
Evidencia: fuente + evaluación. Versión v0.1.
Estado PROPOSED.

### R-CK-005 — Vigencia, obsolescencia y versionado

Propósito: conocimiento vigente o tratado como obsoleto (P19).
Alcance: conocimiento reutilizado. Obligatoriedad MUST. Severidad
HIGH. Condición: al reutilizar conocimiento. Acción: comprobar
vigencia; ante obsolescencia potencial: revalidar, marcar obsoleto
o descartar; versionar cuando su naturaleza lo requiera (qué/cuándo/
por qué/impacto/evidencia). Restricción: prohibido asumir vigencia
por antigüedad o familiaridad. Excepción: solo vía mecanismo formal
§10 (autoridad mínima C04+). Evidencia: estado de
vigencia + versión. Versión v0.1. Estado PROPOSED.

### R-CK-006 — Distinciones explícitas

Propósito: §8 operativo; nada implícito se vuelve hecho (P06).
Alcance: todo elemento informativo. Obligatoriedad MUST. Severidad
HIGH. Condición: al clasificar información. Acción: etiquetar cada
elemento FACT/KNOWLEDGE/CONTEXT/MEMORY/ASSUMPTION/DECISION/EVIDENCE.
Restricción: prohibida la conversión silenciosa memoria→hecho y
supuesto→requisito. Excepción: ninguna. Evidencia: etiquetas.
Versión v0.1. Estado PROPOSED.

### R-CK-007 — Contradicciones entre fuentes

Propósito: resolver sin regla implícita de "lo más reciente gana".
Alcance: fuentes en desacuerdo. Obligatoriedad MUST. Severidad HIGH.
Condición: al detectar contradicción. Acción: clasificar (menor,
versiones, desactualización, distinta autoridad, crítica);
ponderar autoridad+fuente+alcance+contexto+vigencia; resolver o
STOP→ESCALATE si es crítica e irresoluble. Restricción: prohibido
elegir por recencia sin ponderar. Excepción: ninguna para la
clasificación. Evidencia: análisis + resolución/escalado. Versión
v0.1. Estado PROPOSED.

### R-CK-008 — Insuficiencia e incertidumbre crítica

Propósito: sin información crítica suficiente no se continúa (P06,
P14). Alcance: toda Task. Obligatoriedad MUST. Severidad CRITICAL.
Condición: distinguir NO HAY INFORMACIÓN / INSUFICIENTE /
SUFICIENTE e INCERTIDUMBRE ACEPTABLE vs CRÍTICA. Acción: si crítica:
NO INVENTAR, NO SUPONER, NO OCULTAR, NO CONTINUAR SILENCIOSAMENTE →
stop/escalado R-GB-008/009. Restricción: prohibido continuar por el
mero hecho de que exista alguna información. Excepción: ninguna.
Evidencia: evaluación de suficiencia + stop/escalado. Versión v0.1.
Estado PROPOSED.

### R-CK-009 — Preservación y anti-memoria-implícita

Propósito: el conocimiento relevante sobrevive a la sesión (P18,
P30). Alcance: conocimiento que cambia decisiones, restringe,
explica excepciones, permite continuar, evita reinvestigar o
reconstruir contexto. Obligatoriedad MUST. Severidad HIGH. Condición:
al generarlo. Acción: asegurar que pueda recuperarse posteriormente
vinculado a su origen, decisión y evidencia; nada importante depende
solo de memoria implícita. El CÓMO (formato, registro sistemático,
mantenimiento, gobierno documental) lo define F1-S10: F1-S3 establece
QUÉ debe preservarse y POR QUÉ. Restricción:
prohibida la preservación selectiva que oculte contexto crítico.
Excepción: solo vía mecanismo formal §10 (autoridad mínima C04+).
Evidencia: vínculo origen/decisión/evidencia. Versión v0.1.
Estado PROPOSED. Relación: base para RC-09 (F1-S10), sin sistema
técnico KB.

### R-CK-010 — Continuidad y trazabilidad conceptual

Propósito: cadena TASK→CONTEXT→KNOWLEDGE→DECISION→EVIDENCE como
obligación operativa. Alcance: conocimiento relevante por Task.
Obligatoriedad MUST. Severidad HIGH. Condición: al cerrar o
traspasar trabajo. Acción: vincular cada pieza a origen, decisión y
evidencia para continuidad entre Tasks. Restricción: prohibidos
eslabones huérfanos en conocimiento crítico. Excepción: solo vía
mecanismo formal §10 (autoridad mínima C04+).
Evidencia: cadena vinculada. Versión v0.1. Estado PROPOSED.
Relación: obligación, no infraestructura (RC-09 la opera).

## 10. Excepciones

Rigen `RULE-GOVERNANCE.md` §1 (9 campos, C04+/C05+, duración,
revisión, revocación). Ninguna Rule RC-02 admite excepción informal.
Aplica a todas las menciones de excepción en las fichas (§9):

La Rule solo puede ser exceptuada mediante el mecanismo formal de
excepción definido por F1-S1 y la gobernanza aplicable, con la
autoridad, alcance, duración, evidencia y revisión correspondientes.
Una excepción no ocurre automáticamente, no elimina la Rule, requiere
autoridad válida formalmente autorizada, tiene alcance definido y
duración o revisión, deja evidencia, puede ser revocada y no permite
modificar silenciosamente la autoridad normativa. Los niveles C04+ /
C05+ citados indican autoridad mínima dentro de ese mecanismo, nunca
permiso automático para ignorar la Rule.

Aprobar una Rule no autoriza a exceptuarla: la aprobación recorre el
lifecycle F1-S1; cada excepción es una decisión separada con su
propia autoridad, alcance, duración y evidencia. Quien puede aprobar
no obtiene por ello permiso permanente de excepción.

## 11. Precedencia

Orden F1-S1 §2; RC-02 especializa RC-01 en contexto/conocimiento.
Colisión irresoluble: CONFLICT→…→HUMAN DECISION (F1-S1). Sin
arbitrariedad.

## 12. Dependencias

R-GB-002/003/006/008/009/010 (PROPOSED, declarado), P12/P18/P19,
F0-S5 (estados), F0-S7 (C-niveles). Grafo acíclico; sin circulares.
(P24 —privacidad y datos sensibles— pertenece a RC-06 Seguridad; no
es dependencia normativa de RC-02.)

## 13. Evidencia

Sub-bloque WHAT/WHEN/WHO/WHY/RESULT/SOURCE por Rule + responsable y
momento (en cada ficha). `Evidence ≠ Validation ≠ Authorization ≠
Decision`.

## 14. Estado de Rules

Las 10: PROPOSED v0.1. Sin enforcement; sin ACTIVE automático.

## 15. Versionado

`vMAYOR.menor` F1-S1 §5; historial desde v2.

## 16. Historial

Inicial en todas (sin sustituciones).

## 17. Relación con futuras categorías

RC-09 opera la preservación/traza (R-CK-009/010 base); RC-04/RC-10
fijan formas de validación/cierre; RC-07 detalla recovery; RC-08
gates. Referenciadas, no invadidas. Necesidades de otras categorías:
documentadas como dependencia/fuera de alcance, no implementadas.

## 18. Criterios de validación

A01–A23 en `F1-S3-VALIDATION.md`.
