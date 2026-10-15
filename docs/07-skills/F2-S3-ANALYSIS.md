# F2-S3-ANALYSIS — Sprint Analysis (SK-ANL-001)

## 1. Identificación

F2-S3, Bloque B, dominio `analysis`, Skill `SK-ANL-001` v0.1 PROPOSED. Estado: en auditoría, pendiente de supervisión humana (no aprobado/certificado).

## 2. Propósito

Primera capacidad principal Factory-native: análisis previo verificable y trazable que reduce incertidumbre para Planning y posteriores.

## 3. Alcance

§§7–20 del contrato implementado (entradas, procedimiento 15 pasos, epistemología FACT/INFERENCE/ASSUMPTION/UNCERTAINTY/DECISION, dependencias, impacto, riesgos, alternativas, outputs, evidencia, validación, fallos, gates, traza). Incluye APIs/datos/migraciones/despliegues como objeto, sin implementarlos.

## 4. Fuera de alcance

Planning y posteriores, Agents, Runtime/Adapter, Orchestrator, composición F2-S15, infra/CI-CD, Git-ops, F1/F2-S1/F2-S2 (intactos).

## 5. Relación con F0/F1-S1/F2-S2

Contrato 18 campos F2-S1 instanciado; convención F2-S2 (`skills/analysis/SK-ANL-001.md` + `.validation.md`, INDEX); Related Rules citadas sin copiar (R-GB/R-CK/R-MS/R-TQ/R-SP/R-ER/R-AH, 22/22 verificadas existentes).

## 6. Relación con F2-S2

Ubicación, nomenclatura, versionado v0.1, Requires/Provides, índice. Sin rediseño.

## 7. Relación con F1-S2

Complementa R-GB-001/002/003/006/007/008/009/010 sin duplicarlos.

## 8. Definiciones conceptuales

FACT (evidencia) ≠ INFERENCE (derivada) ≠ ASSUMPTION (etiquetado, nunca requisito) ≠ UNCERTAINTY ≠ DECISION (autoridad). Estados: Known/Unknown/Missing/Assumed/Confirmed/Contradictory.

## 9. Rules RC-02+ aplicadas

R-CK-006/008 (clasificación, insuficiencia), R-GB-002 (no inventar), R-AH-005 (gates), R-MS-001 (alcance).

## 10. Excepciones

Ninguna invocada; mecanismo formal disponible sin uso.

## 11. Precedencia

Contrato F2-S1 > convención F2-S2 > validación propia; Rules F1 como norma externa citada.

## 12. Dependencias

F2-S1, F2-S2, INDEX, 22 Rules F1 (existentes), P03/P06/P09/P10/P12/P13/P14/P18/P19. Grafo acíclico.

## 13. Evidencia

`SK-ANL-001.validation.md` + greps de IDs/dependencias + git status/diff --check.

## 14. Estado

SK-ANL-001 v0.1 PROPOSED; validación VERIFIED técnica; INDEX coherente (fila = archivo).

## 15. Versionado

v0.1 inicial 2026-10-12; Changelog en Skill; Git como historial.

## 16. Historial

Definición inicial (este sprint); sin sustituciones. Rechazo previo de F2-S3 no reutilizado: artefactos actuales creados de nuevo, sin restos.

## 17. Relación con futuras categorías

Planning consume outputs; resto referenciado, no invadido.

## 18. Criterios de validación

35 criterios originales en `F2-S3-VALIDATION.md` (31 técnicos PASS con evidencia; 32–35 PENDING HUMAN REVIEW).
