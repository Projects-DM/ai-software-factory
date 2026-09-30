# RUNTIME-DECOUPLING-AUDIT — Auditoría de desacoplamiento y portabilidad

Naturaleza: read-only. Rama `operativo` (base: merge #61 F1-S4).
Método: inventario de archivos, 33 menciones OpenCode, 0 configs de
runtime, clasificación D0–D3 con evidencia. Sin modificaciones.

## 1. Objetivo y arquitectura objetivo

Determinar si la Factory construye arquitectura propia con OpenCode
como runtime o arquitectura dependiente de OpenCode. Objetivo:
`FACTORY ≠ OPENCODE`, `AGENT ≠ RUNTIME`, `SKILL ≠ RUNTIME`,
`RULE ≠ RUNTIME`, `STATE ≠ AGENT MEMORY`, `KNOWLEDGE ≠ SESSION
CONTEXT` — OpenCode-first, no OpenCode-dependent.

## 2. Inventario (evidencia)

- Archivos: ~40 Markdown + 3 Mermaid; 0 código, 0 `.opencode/`, 0
  `opencode.json(c)`, 0 `SKILL.md`, 0 permisos/prompts/sesiones.
- 33 menciones OpenCode: todas documentales-posicionales (entorno
  actual reemplazable; `OpenCode ≠ Tools`; P21). Cero técnicas.
- Rules (29: R-GB-001…011, R-CK-001…010, R-MS-001…008): 0 menciones
  OpenCode salvo la separación normativa `OpenCode≠Tools` (F1-S3:35).
- Estado: Git (commits/PRs #46–#61) + documentos versionados; P18
  prohíbe conocimiento solo-en-sesión.

## 3. Matriz D0–D3

| ID | Componente | Dependencia | Tipo | Nivel | Evidencia | Impacto | Solución |
|----|-----------|-------------|------|-------|-----------|---------|----------|
| RP-001 | Rules (29) | ninguna | normativa | D0 | 06-rules/*.md; 0 menciones runtime | bajo | mantener |
| RP-002 | Principles/lifecycle/gates/gobernanza | ninguna | normativa | D0 | 01-foundations, 03-workflow, 05-decisions | bajo | mantener |
| RP-003 | Taxonomía/contrato/ADR | ninguna | normativa | D0 | 06-rules/RULE-*.md | bajo | mantener |
| RP-004 | Estado Git + historia | ninguna | registro | D0 | log #46–#61; F0-S4 C12/C13 | bajo | mantener |
| RP-005 | Markdown/Mermaid | ninguna | formato | D0 | 40+ docs versionados | bajo | mantener |
| RP-006 | OPENCODE.md (posición) | mención entorno actual | documental | D1 | 04-tools/OPENCODE.md:7–10 | medio | espejar por runtime futuro |
| RP-007 | toolchain.mmd nodo OC | nodo diagrama | diagrama | D1 | 04-tools/toolchain.mmd:12 | medio | nodo por runtime tras adapter |
| RP-008 | Baseline CORE | OpenCode listado sustituible | gobernanza | D1 | TOOLING-BASELINE:54,71; sustitución §5 | medio | aplicar C01–C12 al sustituir |
| RP-009 | Formato Skill futuro | `SKILL.md` vs Factory-native indeciso | formato | D1 | sin Skills existentes; F2 pendiente | medio | decidir formato en F2 (REC-03) |
| RP-010 | Contrato Agent futuro | parámetros runtime-specific sin fijar | formato | D1 | AGENTS.md conceptual; F3 pendiente | medio | separar contrato/adapter en F3 |

D2: 0. D3: 0. Sin acoplamiento técnico porque nada está implementado.

## 4. Preguntas críticas (resumen)

Fábrica: Rules, principios, lifecycle, gobernanza, conocimiento,
Tasks, estado Git, evidencia. Runtime: ejecución de modelo,
herramientas y contexto de sesión. Frontera clara SÍ; adapter
conceptual NO existe aún (propuesto en recomendaciones). OpenCode
directo: 33 menciones posicionales; indirecto: operación de-facto en
sesiones OpenCode (disciplina P18 manual). Skills: definibles
independientes SÍ; decidir formato en F2. Agents: contrato portable
SÍ (AGENTS.md); parámetros runtime-specific a aislar en F3. Estado/
decisiones/evidencia: Git+docs; si un agente desaparece, otro
continúa desde la traza (pérdida acotada a trabajo no registrado en
sesión). Multi-agent A→B SÍ por diseño; cambio de modelo/proveedor/
runtime SÍ si cumplen el Factory Contract. Si OpenCode dejara de
convenir: migrarían sesiones y nodo diagrama; intactos Rules,
conocimiento, estado, gobernanza (esfuerzo bajo mientras no exista
implementación acoplada).

## 5. Riesgos

R1 De-facto single runtime: todo ocurre en sesiones OpenCode; la
externalización depende de disciplina humana (WARNING).
R2 Formato Skill por defecto: si F2 implementa sin decidir formato,
`SKILL.md`-shape se vuelve estándar de facto (D1→D2).
R3 Memoria de sesión como atajo: bajo presión, contexto crítico
podría quedar sin registrar (P18 lo prohíbe; sin captura
automatizada).
R4 Permisos OpenCode como autoridad: allow/ask/deny son
implementación; la autoridad vive en Rules/C-niveles (aislar vía
mapeo).

## 6. Conclusiones y gate

```text
CURRENT STATE: arquitectura propia con OpenCode como runtime (D0 ×5, D1 ×5, D2 ×0, D3 ×0)
DEPENDENCIES: solo documentales/diagrama/gobernanza; cero técnicas
RISKS: R1–R4 (ningún bloqueante)
MINIMUM REQUIRED CHANGES: 0 bloqueantes; 3 condiciones de entrada F2/F3 (documento 2)
PORTABILITY READINESS: apta para continuar a F2 con guardarraíles (documento 3)
```

Respuesta principal: la Factory construye arquitectura propia que
utiliza OpenCode como runtime; no arquitectura dependiente. No
desacoplar por desacoplar: conservar OpenCode y aislar solo la
frontera.
