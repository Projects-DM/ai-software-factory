# RULE-TAXONOMY — F1-S1 Taxonomía de Rules

Fase: F1 — Rules. Sprint: F1-S1. Estado: CONCEPTUAL.
Cada categoría será desarrollada por un sprint F1-S2…F1-S12 (mapeo
indicado). Sin duplicación: lo que pertenece a dos áreas se asigna a
una y se referencia desde la otra.

## RC-01 — Comportamiento general → F1-S2

Propósito: conducta base de todo ejecutor (no inventar, validar antes
de declarar, escalar ante incertidumbre). Alcance: toda Task y agente.
Incluye: deberes transversales P06/P09/P10/P14. NO incluye: conducta
específica de testing, Git o seguridad (RC-04/05/06). Relaciona: todas
como base.

## RC-02 — Contexto y conocimiento → F1-S3

Propósito: contexto mínimo necesario y conocimiento versionado (P12,
P18, P19, P24). Alcance: asignación y uso de contexto por tarea.
Incluye: selección, minimización, registro. NO incluye: ejecución de
herramientas (RC-06/RC-07). Relaciona: RC-09 (documentación).

## RC-03 — Alcance y modificación → F1-S4

Propósito: límites de cambio por tarea; no arreglar una cosa rompiendo
otra (P05, P17). Alcance: diffs, artefactos, configuración tocada.
Incluye: impacto, reversibilidad, preservación. NO incluye: workflow
Git (RC-05). Relaciona: RC-07 (recuperación ante regresión).

## RC-04 — Testing y calidad → F1-S5

Propósito: contraste contra criterios antes de avanzar (P03, P04,
P25). Alcance: TESTING/REVIEW del lifecycle. Incluye: veredictos,
cobertura exigible, certificación. NO incluye: revisión humana de
puertas (RC-08). Relaciona: RC-10 (certificación).

## RC-05 — Git y GitHub → F1-S6

Propósito: versionado, ramas, PRs, merges como nodos de traza (P13,
P19). Alcance: repositorio e integración. Incluye: commits vinculados
a Task, PR con evidencia, merge verificado. NO incluye: despliegue de
producto (fuera de Factory). Relaciona: RC-09, RC-10.

## RC-06 — Seguridad y permisos → F1-S7

Propósito: least privilege y seguridad por diseño (P09, P23, P24).
Alcance: agentes, Skills, herramientas, Git, integraciones. Incluye:
permisos mínimos/explícitos, secretos fuera de Git/logs. NO incluye:
autonomía (RC-08). Relaciona: RC-02 (minimización de datos).

## RC-07 — Errores y recuperación → F1-S8

Propósito: fallo seguro y recuperación diagnosticada (P14–P17).
Alcance: FAILED/RECOVERING/BLOCKED. Incluye: clasificar, preservar,
diagnosticar, recuperar/validar, no-reintento-ciego. NO incluye:
testing preventivo (RC-04). Relaciona: RC-03, RC-05.

## RC-08 — Autonomía e intervención humana → F1-S9

Propósito: delegación por evidencia con Human Gates (P01, P02, P26).
Alcance: niveles 1–4, puertas, escalamiento. Incluye: límites
delegables, gates obligatorios, WAITING_HUMAN. NO incluye: testing
(RC-04). Relaciona: RC-06 (autoridad), RC-01 (escalar).

## RC-09 — Documentación y trazabilidad → F1-S10

Propósito: traza extremo a extremo y conocimiento persistente (P13,
P18, P19). Alcance: cadena Task→…→resultado. Incluye: vínculos
obligatorios, artefactos versionados. NO incluye: certificación de
entrega (RC-10). Relaciona: RC-05, RC-02.

## RC-10 — Finalización y certificación → F1-S11

Propósito: cierre válido (CERTIFIED/COMPLETED/CLOSED) sin declarar
éxito sin evidencia. Alcance: INTEGRATE/DEPLOY/estados finales.
Incluye: criterios de cierre, archivo. NO incluye: despliegue de
producto. Relaciona: RC-04, RC-05, RC-09.

## RC-11 — Gobierno y evolución → F1-S12

Propósito: cambio gobernado de la propia Factory (P20, P26, F0-S7).
Alcance: Rules, Skills, Agents, arquitectura. Incluye: ADR C04+,
versionado, superseding, medición previa (P25). NO incluye: reglas de
producto. Relaciona: todas (meta-categoría).
