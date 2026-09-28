# F1-S1-VALIDATION — Matriz de aceptación y prueba principal

Fase: F1 — Rules. Sprint: F1-S1. Método: criterio → artefacto →
evidencia → resultado. Sin evidencia no hay PASS.

| Criterio | Artefacto | Evidencia | Resultado |
|----------|-----------|-----------|-----------|
| Definición formal de Rule | RULE-CONTRACT §1 | validez iff + tabla 10 artefactos | PASS |
| Contrato | RULE-CONTRACT §3 | 20 campos especificados | PASS |
| Taxonomía | RULE-TAXONOMY | RC-01…RC-11 sin duplicación + mapeo F1-S2…S12 | PASS |
| Obligatoriedad | RULE-CONTRACT §4 | MUST/MUST NOT/SHOULD/MAY/HUMAN APPROVAL + SHOULD≠MUST | PASS |
| Severidad | RULE-CONTRACT §5 | escala + 5 no-confusiones | PASS |
| Alcance | RULE-CONTRACT §6 + campo 4 | 10 dimensiones, conceptual | PASS |
| Condiciones | RULE-CONTRACT §6 | Rule/Condition/Action/Restriction + 4 preguntas | PASS |
| Excepciones | RULE-GOVERNANCE §1 | 9 campos + autorización/expiración/revocación | PASS |
| Precedencia | RULE-GOVERNANCE §2 | orden + procedimiento 5 pasos | PASS |
| Resolución de conflictos | RULE-GOVERNANCE §3 | ruta 8 pasos, sin autorización por silencio | PASS |
| Versionado | RULE-GOVERNANCE §5 | semántica + historial, sin edición silenciosa | PASS |
| Lifecycle | RULE-GOVERNANCE §6 | 5 estados + transiciones válidas/inválidas + consulta temporal | PASS |
| Activación | RULE-GOVERNANCE §7 | condiciones/autoridad/evidencia/fecha | PASS |
| Desactivación | RULE-GOVERNANCE §7 | idem + vínculo sustituta | PASS |
| Autoridad | RULE-CONTRACT campo 12 | niveles F0-S7 C01–C06, sin roles inventados | PASS |
| Evidencia | RULE-CONTRACT campo 16 | WHAT/WHEN/WHO/WHY/RESULT/SOURCE + 3 desigualdades | PASS |
| Dependencias | RULE-GOVERNANCE §8 | nodos versionados, sin circulares | PASS |
| Relación general/específica | RULE-GOVERNANCE §4 | 5 modos + prohibición de eliminación silenciosa | PASS |
| Coherencia con F0 | todos | P01–P29 citados; AGENTS/cadena; sin redefinir F0 | PASS |

## Prueba principal

> ¿Puede otra persona diseñar una Rule nueva usando solo este contrato?

SÍ: los 9 ejemplos X-001…X-009 instancian cada dimensión (MUST,
MUST NOT, SHOULD, MAY, HUMAN APPROVAL, excepción, dependencia,
evidencia, general/específica) usando exclusivamente campos del
contrato, sin inventar estructura. Nada falta del alcance F1-S1;
ningún BLOCKED.
