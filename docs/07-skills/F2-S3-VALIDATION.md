# F2-S3-VALIDATION — Matriz de aceptación (auditoría R5)

Sprint: F2-S3 (+ R1, R2, R3, R4, R5). Fecha: 2026-10-13. Versión: v0.1. Estado: READY FOR HUMAN REVIEW (no aprobado/certificado).
Archivos: existentes `skills/analysis/SK-ANL-001.md`, `.validation.md`, `skills/INDEX.md`; creados `docs/07-skills/F2-S3-ANALYSIS.md`, `docs/07-skills/F2-S3-VALIDATION.md`; ajenos intactos. Rama `feature/f2-s3-analysis`.
Método: [A]utomático (grep/conteo/comandos), [S]emántico (lectura íntegra del contenido exigido), [H]umano (pendiente). Criterios originales: especificación F2-S3 §36 (texto en historial operativo; sin fichero canónico separado — limitación registrada).
Formato: ID | requisito original | tipo | artefacto (ubicación) | condición | método | evidencia | resultado | hallazgo/corrección.

## Capacidad

- 01 | Analysis es una capacidad reutilizable. | técnico | SK §§5–6 | neutralidad tech | [S] | tech-neutral, sin Agent/Runtime/modelo/herramienta | PASS | — | —
- 02 | Cumple F2-S1. | técnico | SK 18 campos | presencia+sustancia | [A]+[S] | 18 encabezados + contenido verificado | PASS | — | —
- 03 | Es Factory-native. | alcance | SK §§5,11 | sin runtime | [A] | 0 dependencias estructurales | PASS | — | —
- 04 | Es independiente de Agents. | alcance | SK §6 Fuera | [S] | exclusión explícita | PASS | — | —
- 05 | Es independiente de Runtime. | alcance | SK §6 Fuera | [S] | exclusión explícita | PASS | — | —
- 06 | OpenCode no es dependencia estructural. | alcance | SK, 0 menciones | [A] | grep vacío | PASS | — | —
- 07 | No depende de un modelo/proveedor concreto. | alcance | §5 neutral | [S] | sin modelo/proveedor | PASS | — | —
- 08 | No depende de una herramienta concreta salvo deliberadamente acotada. | alcance | §11 sustituibles | [S] | medios genéricos | PASS | — | —

## Contrato

- 09 | Inputs definidos. | documental | SK §9 | 10 entradas + faltantes + B1–B3 | [S] | texto verificado | PASS | — | —
- 10 | Outputs definidos. | documental | SK §12 | 20 campos + 6 estados asignados | [S] | texto verificado | PASS | asignación R3 | —
- 11 | Requires/Provides definidos. | documental | §12 consumible | [S] | consumible declarado | PASS | — | —
- 12 | Procedimiento reproducible. | documental | §10, 15 pasos | [A]+[S] | 15 contados + cierre trazable | PASS | — | —

## Razonamiento

- 13 | Facts/Inferences/Assumptions distinguibles. | documental | §§8,10.3/8/9 | 5 tipos + 6 estados + 7 ejemplos | [S] | texto verificado | PASS | modelo R2 | —
- 14 | Requisitos faltantes identificables. | documental | §9 + §15 | registro+escalado | [S] | texto verificado | PASS | — | —
- 15 | Incertidumbres registrables. | documental | §9 + §13 + §15 | tratamiento | [S] | texto verificado | PASS | — | —
- 16 | Dependencias e impactos analizables. | documental | §§10.6/10 + §11 | [S] | texto verificado | PASS | — | —
- 17 | Riesgos registrables. | documental | §10.7, 9 subcampos | [S] | conteo + anti-invención | PASS | — | —
- 18 | Alternativas documentables sin decisión automática. | documental | §10.11 sin decidir | [S] | texto verificado | PASS | — | —

## Gobernanza

- 19 | Human Gates definidos. | gobernanza | §16 + R-AH-005 (gates) | [A]+[S] | ID existe + pertinencia verificada | PASS | — | —
- 20 | Evidence definida. | documental | §14 base≠suficiencia | [S] | texto verificado | PASS | — | —
- 21 | Validation definida. | documental | §13 reproducible | [S] | checklist con métodos | PASS | — | —
- 22 | Failure / uncertainty handling definido. | documental | §15 + STOP/ESCALATE/WAIT | [S] | texto verificado | PASS | — | —
- 23 | Traceability definida. | documental | Objective→Next State, P13 | [S] | cadena verificada | PASS | — | —

## Reutilización

- 24 | Reutilizable en distintos contextos. | alcance | §5 neutral | [S] | 10 contextos por diseño | PASS | — | —
- 25 | Compatible con F2-S2. | gobernanza | ubicación/nomenclatura/versionado/índice | [S]+status | convención cumplida | PASS | v0.1 + PROPOSED justificados | —
- 26 | Compatible con F1. | gobernanza | 22/22 IDs + texto operativo leído (Propósito/Acción/Condición/Restricción de cada una) | [A] grep + [S] lectura íntegra | PASS | 22/22 contrastadas R6 (12 R5 + 10 restantes) | —
- 27 | No implementa Agents ni Runtime Adapter. | alcance | §6 Fuera | [A] | 0 implementaciones | PASS | — | —
- 28 | No adelanta F2-S4 ni Skills posteriores. | alcance | Planning consumidor | [S] | sin diseño Planning | PASS | — | —
- 29 | No introduce contradicciones críticas. | gobernanza | barrido §§1–18 | [S] | 0 halladas | PASS | — | —

## Técnica y humanos

- 30 | Validación técnica PASS. | técnico | diff --check limpio; 5 artefactos | [A] comandos | PASS | salida vacía + status acotado | — | —
- 31 | Evidencia suficiente para revisión humana. | documental | este documento + `.validation.md` | [S] inspección | PASS | expediente completo | — | —
- 32 | Human Review. | humana | — | decisión reservada | [H] pendiente | PENDING HUMAN REVIEW | — | pendiente
- 33 | Human Approval. | humana | — | decisión reservada | [H] pendiente | PENDING HUMAN REVIEW | — | pendiente
- 34 | Git Versioning / Integration. | humana | — | flujo autorizado | [H] pendiente | PENDING HUMAN REVIEW | — | pendiente
- 35 | F2-S3 Integration. | humana | — | cierre formal | [H] pendiente | PENDING HUMAN REVIEW | — | pendiente

## Casos semánticos §6 (R4/R5, re-verificados R6)

- A (completo+validado+suficiente) → completado-validado, Next recomendado. PASS [S].
- B (completo+validado+insuficiente por decisión) → completado-insuficiente, suficiencia FALSA, Next escalado. PASS [S].
- C (parcial + contradicción material) → bloqueado por orden (contradicción > parcialidad), cobertura registrada. PASS [S].
- D (fallo de validación por falta de evidencia) → no-validado + revalidación requerida. PASS [S].
- E (interrupción externa sin bloqueo) → interrumpido con punto y estado. PASS [S].
- F (interrupción tras bloqueo crítico) → bloqueado (orden), interrupción como dimensión registrada. PASS [S].
- G (validado sin autorización posterior) → completado-validado + autorización FALSA, Next solo recomendado. PASS [S].
- H (nueva evidencia contradice conclusión) → re-clasificación (bloqueado/no-validado) + historial preservado. PASS [S].

## Coherencia J

Contrato/validación/INDEX/sprint-docs/contrato/arq/Rules coherentes; INDEX PROPOSED conservado (convención F2-S2: Status descubre, no aprueba); versión v0.1 conservada (cambios compatibles R1–R6; MAYOR solo ante cambio normativo); sin Agents/adapter/composición; 22/22 Rules re-verificadas (existencia R1/R2/R4; semántica R4/R5/R6).

## Verificación final §16

Artefactos íntegros; 18 campos; 15 pasos; epistemología con ejemplos; B1–B3 + orden de evaluación; estados con asignación + 8 casos; runtime-free; Rules (12 contrastadas semánticamente); matriz 35/35 (31 PASS + 4 pendientes humanos); índice; diff --check limpio; status con solo cambios F2-S3; sin artefactos ajenos. Fechas: inicial 2026-10-12, refinamientos 2026-10-13 (= hoy, sin futurismo); SK validación 2026-10-12 = validación inicial (histórico preservado). Limitación: spec §36 en historial operativo.
Bloqueos: 0. Dictamen: **READY FOR HUMAN REVIEW**.
Historial: v0.1 auditoría + R1 + R2 + R4 + R5 + R6 (2026-10-13).
