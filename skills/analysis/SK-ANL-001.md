# SK-ANL-001 — Analysis

## 1. ID

`SK-ANL-001`

## 2. Name

Analysis

## 3. Version

`v0.1` (inicial; Changelog §18).

## 4. Purpose

Transformar información disponible sobre una necesidad, problema, sistema o cambio propuesto en un resultado estructurado que facilite la toma de decisiones y la preparación de trabajo posterior: contexto estructurado, hechos, requisitos, restricciones, dependencias, riesgos, incertidumbres, supuestos explícitos, preguntas abiertas, impactos, alternativas, hallazgos, evidencia, recomendaciones y condiciones para avanzar. Principio: **no modificar antes de comprender**.

## 5. Capability

Análisis previo a la acción sobre necesidades, problemas, sistemas, cambios o situaciones. Capacidad abstracta y tecnológicamente neutra: sin lenguaje, framework, herramienta, modelo, runtime, repositorio ni tecnología.

## 6. Scope

Análisis funcional y técnico; contexto; requisitos existentes, faltantes y ambiguos; restricciones; dependencias; impacto; riesgos; supuestos; incertidumbres; preguntas abiertas; alternativas; incompatibilidades; contradicciones; hallazgos; evidencia; validación del análisis; preparación para Planning; documentación trazable. Incluye análisis aplicable a APIs, datos, migraciones, despliegues e infraestructura **como objeto de análisis**, sin implementarlos. Fuera: Planning, Architecture, Implementation, Database Engineering, Testing, Code Review, Debugging, Release/Deploy, Agents, Runtime/Adapter, Orchestrator, autorización automática, decisión humana, acciones destructivas.

## 7. Preconditions

1. Objetivo o problema identificado. 2. Contexto disponible. 3. Capacidad técnica de inspección. 4. Herramientas de lectura disponibles. 5. Autorización aplicable existente (verificada, nunca presunta; existencia de herramienta o permiso técnico ≠ autorización). 6. Alcance de la autorización conocido. 7. Restricciones de acceso conocidas. 8. Estado compatible del objeto de análisis. Comportamiento: comprobar las aplicables; no presumir ausentes; registrar la carencia; no realizar la operación no autorizada (su falta no autoriza vías alternativas); escalar cuando corresponda; conservar evidencia disponible sin vulnerar restricciones.

## 8. Required Context

Mínimo necesario, identificable y vigente: objetivo/problema, alcance, artefactos y estado disponibles, restricciones conocidas, stakeholders cuando corresponda.

Modelo epistemológico (compatible con los campos del contrato, sin campos nuevos). Tipos: FACT (evidencia identificable y verificable exigible), INFERENCE (hechos fuente + razonamiento explícitos), ASSUMPTION (declarada expresamente; jamás requisito confirmado), UNCERTAINTY (qué no se sabe + consecuencia), DECISION (decisión + autoridad + estado cuando disponibles). Estados (no solapados): Known = observado y registrado; Confirmed = verificado contra evidencia; Missing = requerido pero no proporcionado; Unknown = no determinable con lo disponible; Assumed = etiqueta provisional; Contradictory = afirmaciones incompatibles que exigen ruta de resolución (nunca simple desconocido). Cada pieza: (1) tipo, (2) estado, (3) evidencia o procedencia, (4) incertidumbre o contradicción, (5) decisión pendiente si aplica. Ninguna inferencia como observación directa, ninguna hipótesis como hecho, ninguna propuesta como decisión aprobada; ninguna ASSUMPTION se transforma silenciosamente en requisito. Ejemplos: (1) lectura de un archivo versionado → FACT/Known; (2) "el módulo X depende de Y porque ambos importan Z" → INFERENCE/Known con fuentes; (3) latencia no medida → UNCERTAINTY/Unknown; (4) requisito de negocio no entregado → ASSUMPTION/Missing si se continúa explícitamente, o Missing puro con escalado; (5) "supongamos ventana de 2s" → ASSUMPTION/Assumed; (6) "usa OAuth" vs "usa API keys" → Contradictory con resolución; (7) cambio pendiente del comité → DECISION con estado pendiente y autoridad.

## 9. Inputs

Objetivo o problema; contexto disponible; requisitos existentes; documentación; restricciones conocidas; estado actual del sistema; evidencia existente; cambio solicitado; dependencias conocidas; información de stakeholders. Faltantes → `Missing Information / Unknown / Uncertainty / Open Question`. Continuación permitida (B1) solo dentro de alcance con precondiciones y autorizaciones vigentes. Resultado parcial/limitado (B2) permitido sin ocultar faltantes ni presentar lo incompleto como definitivo, con límites registrados. Bloqueo/escalado (B3) ante: información crítica ausente, contradicciones materiales, autorización insuficiente o ambigua, dependencias no verificadas que alteren conclusiones, riesgos críticos, incertidumbre material, decisiones humanas pendientes, fallos de validación o acciones fuera de alcance. Recopilar información ≠ ejecutar acciones que requieran autorización adicional; la Skill no acepta riesgos críticos ni decide negocio/arquitectura reservados.

## 10. Procedure

1. Understand Objective. 2. Collect Available Context. 3. Identify Facts (solo lo observado/verificable). 4. Identify Requirements (existentes, faltantes, ambiguos). 5. Identify Constraints. 6. Identify Dependencies (documentarlas no autoriza actuar sobre ellas). 7. Identify Risks (descripción, causa, impacto, probabilidad razonable, severidad, evidencia, mitigación, decisión requerida, estado de la información; estimaciones con base explicable e incertidumbre registrada; sin cifras inventadas; la falta de información no implica ausencia de riesgo; mitigaciones propuestas ≠ ejecutadas; la aceptación requiere autoridad identificada; riesgo crítico → escalado según Rules). 8. Identify Assumptions (etiquetados, nunca requisitos). 9. Identify Uncertainties. 10. Analyze Impact (funcionalidad, arquitectura, datos, seguridad, rendimiento, compatibilidad, testing, documentación, operación, mantenimiento, despliegue; `Impact Analysis ≠ Authorization`). 11. Evaluate Alternatives (`A/B/C → Evidence → Trade-offs → Decision Required`, sin decidir). 12. Produce Findings. 13. Record Evidence. 14. Validate Analysis. 15. Produce Consumable Output. Contradicción → DETECT → DOCUMENT → ASSESS IMPACT → ESCALATE IF NECESSARY. Reproducible y abstracto de herramienta. Cierre: si la validación falla, falta evidencia o aparece contradicción material, el resultado se cierra trazablemente como parcial, insuficiente, bloqueado o no validado (nunca como completo y validado); pasos 11–15 determinan el estado final sin crear pasos nuevos.

## 11. Tools

Medios de lectura/inspección sustituibles, declarados por ejecución; `TOOL ≠ SKILL`. Ninguna herramienta concreta forma parte de este contrato; un ejemplo operativo, de existir, queda separado del contrato conceptual.

## 12. Outputs

Analysis ID, Objective, Context, Facts, Requirements, Constraints, Dependencies, Risks, Assumptions, Uncertainties, Open Questions, Impact, Alternatives, Findings, Recommendations, Evidence, Validation, Blockers, Decisions Required, Next Action. Estados de resultado (cada uno: condiciones necesarias, evidencia mínima, exclusiones, relación con validación, bloqueos, decisiones pendientes, Next Action):
- completado-validado: ejecución íntegra + validación superada + suficiente para avanzar; evidencia: validación superada trazada; excluye bloqueos abiertos y decisiones pendientes bloqueantes; Next Action: paso permitido recomendado.
- completado-insuficiente: ejecución íntegra + validación superada o parcial + suficiencia FALSA (p. ej. falta decisión humana); evidencia: brecha identificada; Next Action: escalado/espera, nunca avance.
- parcial: cobertura incompleta declarada con límites registrados; evidencia: alcance cubierto vs pendiente; Next Action: completar o escalar.
- bloqueado: condición crítica impide continuar (incluye contradicción material irresuelta e interrupción externa tras bloqueo); evidencia: causa + estado preservado; Next Action: desbloqueo o escalado.
- no-validado: validación fallida o no concluyente, o falta de evidencia para validar; evidencia: fallo/carencia + revalidación requerida; Next Action: corregir y revalidar.
- interrumpido: detención externa sin fallo propio; evidencia: punto de interrupción + estado; Next Action: reanudar si procede.
Cada estado combina 6 dimensiones independientes (ejecución, validación, suficiencia, bloqueos, decisiones pendientes, autorización posterior); coincidiendo varias, rige el orden: seguridad/bloqueo > fallo de validación > contradicción irresuelta > insuficiencia > interrupción > completado-validado — sin perder las demás dimensiones (todas quedan registradas). Un campo sin contenido aplicable se marca `no identificado`/`no aplicable justificado` (nunca implica inexistencia demostrada); `Next Action` es recomendación del siguiente paso permitido, no autorización para ejecutarlo. Recomendaciones ≠ decisiones aprobadas; evidencia ≠ validación. Consumible por Planning (y Database Engineering, Debugging, Documentation, Validation); `output ≠ success`. Sin convertir Analysis en capacidades posteriores.

## 13. Validation

Lista reproducible (formato por ítem: requisito · conformidad · evidencia · método [A]utomático/[S]emántico/[H]umano · resultado · no-conformidad): objetivo comprendido y delimitado [S]; contexto trazado [S]; hechos/inferencias/supuestos clasificados [S]; 0 requisitos inventados [S]; faltantes registrados [A]; incertidumbres tratadas [S]; dependencias evaluadas [S]; impactos analizados [S]; riesgos justificados [S]; alternativas evaluadas [S]; hallazgos con respaldo [S]; correspondencia evidencia-conclusiones [S]; consistencia [S]; bloqueos registrados [A]; decisiones pendientes identificadas [S]; output suficiente para el consumidor [H]. Veredictos: superada, fallida (requiere corrección y revalidación), bloqueada por falta de evidencia (requiere aportación o escalado), pendiente de evaluación humana (requiere revisor), no aplicable justificada. La validación puede concluir insuficiencia para avanzar sin confundirse con éxito. `EXECUTION ≠ SUCCESS/VALIDATION`; `EVIDENCE ≠ VALIDATION`; `VALIDATION ≠ AUTHORIZATION`.

## 14. Evidence

Documentos/archivos consultados, requisitos, referencias, hallazgos, restricciones, dependencias, inspecciones, decisiones existentes, preguntas abiertas, validación. Demuestra la base del análisis, no su suficiencia.

## 15. Failure Conditions

Contexto insuficiente; precondición incumplida; herramienta ausente; resultado inválido; conflicto; incertidumbre crítica; fallo de validación. Ante crítica: `STOP → PRESERVE EVIDENCE → ESCALATE → WAIT`. Nunca inventar, ocultar, avanzar en silencio, compensar modificando ni convertir hipótesis en hechos.

## 16. Escalation

Faltantes críticos, contradicciones importantes, decisiones de negocio/arquitectura, riesgos críticos, destructivas, incertidumbre material, producción, fuera de alcance. Estructura la necesidad; no asume autoridad.

## 17. Related Rules

R-GB-001/002/003/006/007/008/009/010, R-CK-001/004/006/008/009/010, R-MS-001/003, R-TQ-002/006, R-SP-001, R-ER-002/007, R-AH-005 (`RULES = ALLOWED`, `SKILLS = HOW`; citadas, no copiadas ni redefinidas).

## 18. Changelog

- `v0.1` (2026-10-12): definición inicial F2-S3.
- `v0.1` (2026-10-13, R1+R2+R3+R4+R5): refinamientos compatibles sin cambio normativo (misma versión conforme a F2-S1/F2-S2: MAYOR solo ante cambio normativo/incompatible); semántica y alcance intactos.
