# RULE-GOVERNANCE — F1-S1 Excepciones, precedencia, ciclo de vida

Fase: F1 — Rules. Sprint: F1-S1. Estado: CONCEPTUAL. Sin enforcement
ni automatización. Desarrolla los campos 11, 13–20 del contrato con
base en F0-S7 (sin redefinirlo).

## 1. Excepciones

Registro obligatorio: Rule afectada, Motivo, Condición, Alcance,
Autoridad (C04+ para MUST; C05+ temporal para MUST NOT), Duración
(fecha de expiración explícita), Riesgo, Evidencia, Revisión.
Autorizar, expirar y revocar quedan trazados. Ninguna excepción es vía
informal de ignorar una Rule; la recurrente obliga a revisar la Rule
o el sistema, no a prorrogarla silenciosamente.

## 2. Precedencia

Orden de aplicación ante colisión: (1) mayor autoridad normativa;
(2) específica sobre general dentro de igual autoridad; (3) activa
sobre obsoleta; (4) versión vigente sobre anteriores. Procedimiento:

```text
Detección → Clasificación → Aplicación de precedencia → Validación
→ Continuación, o Escalamiento si no resuelve
```

Ningún agente resuelve por interpretación arbitraria.

## 3. Conflictos no resolubles

```text
CONFLICT → PRESERVE EVIDENCE → STOP / BLOCK → ESCALATE
→ HUMAN DECISION → RESOLUTION → DOCUMENT → CONTINUE
```

Sin autorización por ausencia de información. La resolución documentada
puede motivar nueva Rule o revisión (RC-11).

## 4. General vs específica

La específica complementa, restringe o especializa a la general;
reemplazar exige sustitución versionada con aprobación de la autoridad
de la general; si entra en conflicto rige precedencia. Prohibido
eliminar silenciosamente restricciones críticas generales.

## 5. Versionado e historial

`vMAYOR.menor`: MAYOR = cambio normativo; menor = aclaración. Cada
versión registra qué cambió, quién aprobó, vigencia, versión
sustituida y compatibilidad. Historial preservado (`v2 supersedes
v1`); ninguna modificación relevante es edición silenciosa.

## 6. Ciclo de vida

```text
PROPOSED → UNDER REVIEW → APPROVED → ACTIVE → SUPERSEDED / DEPRECATED
```

- PROPOSED: borrador con campos completos; la mueve el proponente;
  transiciones válidas → UNDER REVIEW (o retirada por el proponente).
- UNDER REVIEW: evaluación contra criterios y evidencia; la mueve el
  revisor del ámbito; → APPROVED o → retirada/rechazo documentado.
  Ninguna Rule opera en este estado.
- APPROVED: aceptada, pendiente de vigencia; la mueve la autoridad
  aprobadora; → ACTIVE en fecha de entrada en vigor.
- ACTIVE: obliga en su alcance. Solo salidas: → SUPERSEDED (nueva
  versión/Rule la sustituye) o → DEPRECATED (retiro con justificación
  y fecha). Transiciones inválidas: ACTIVE → UNDER REVIEW, cualquier
  salto hacia atrás, ACTIVE directa desde PROPOSED.
- SUPERSEDED/DEPRECATED: estados finales, preservados para traza.
  Consulta temporal: la Rule activa en T se determina por historial +
  fechas de vigencia.

## 7. Activación y desactivación

Activación: condiciones cumplidas + autoridad aprobadora + evidencia
de activación + fecha de entrada en vigor. Desactivación: condición
cumplida o decisión + autoridad de igual o mayor nivel + evidencia +
fecha + vínculo con Rule sustituta si existe. Sin automatización en
F1-S1: actos documentales registrados.

## 8. Dependencias

Toda dependencia (Rule, principio, ADR, política, contexto,
artefacto) referencia nodos existentes y versionados; prohibidas
circulares no detectadas (validación: grafo acíclico salvo
referencias históricas a versiones superseded). Depender de una Rule
no ACTIVA exige declararlo y justifica revisión.
