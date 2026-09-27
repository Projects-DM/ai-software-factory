# GITHUB — AI Software Factory — F0-S6 Posición de Git/GitHub

Fase: F0 — Fundaciones.
Sprint: F0-S6 — Herramientas y entorno.
Estado: definición documental y estratégica. No implementa integraciones ni CI/CD.

Git y GitHub son el sistema de registro, revisión e integración de la
Factory (F0-S1, F0-S4 C12/C13/C15): donde el trabajo se versiona, se
revisa, se integra y se recupera. Son entorno actual, no premisa
arquitectónica futura (P21).

## 1. Papel conceptual por capacidad

- Repositories: contenedor versionado de Factory (y, separadamente, de
  cada Product futuro). ACTUAL: este repositorio, verificado.
- Git: registro local de cambios, base de trazabilidad y recuperación.
  ACTUAL, verificado (historial con ramas y merges).
- Branches: aislamiento de trabajo por Task/sprint. ACTUAL, verificado.
- Issues: seguimiento de trabajo vinculado a Tasks.
  PLANIFICADO (posición reservada; uso sistemático pendiente de F0-S7/F4).
  GitHub Issues puede utilizarse posteriormente como mecanismo de
  seguimiento o representación de Tasks, pero Issue no es equivalente
  conceptualmente a Task. `Task ≠ Issue`: la Task es la unidad
  arquitectónica de trabajo (F0-S4 C02, F0-S5); el Issue es una
  herramienta potencial para representarla. No se convierte Issues en
  capacidad actual obligatoria.
- Projects: priorización y visibilidad del flujo. PLANIFICADO.
- Pull Requests: propuesta formal de integración con revisión y
  aprobación humanas. ACTUAL, verificado (PRs #46–#50 mergeados).
- Actions: validación automatizada. NO VERIFICADO en este repositorio
  (sin directorio `.github/` a la fecha): FUTURO, Phase B.
- Releases: hitos versionados de entrega. FUTURO.
- Permissions: quién puede proponer, revisar, aprobar e integrar.
  Conceptuales en F0-S6 (Least Privilege); implementación diferida.
- Traceability: commits, PRs, merges y revisiones son nodos de la traza
  F0-S5, no historia paralela. ACTUAL en su forma manual.
- Evidence: PRs con revisión registrada + merges verificados son
  evidencia de integración. ACTUAL, parcial y manual.

## 2. Relación con el workflow (F0-S5)

```text
Task
→ Branch
→ Implementation
→ Tests
→ Commit
→ Pull Request
→ Automated Checks (FUTURO: hoy revisión humana directa)
→ Review
→ Merge
→ Deploy (FUTURO según alcance de cada Task)
→ Verification
```

Coherente con el lifecycle canónico (DRAFT→…→COMPLETED) y sus estados
excepcionales: BLOCKED/FAILED/RECOVERING se diagnostican con la
evidencia registrada; WAITING_HUMAN puede manifestarse durante revisión,
aprobación o cualquier otro Human Gate aplicable, y su resolución
depende de la decisión autorizada y del estado de origen
(`WAITING_HUMAN ≠ GitHub Review`); CHANGES_REQUESTED es un estado
excepcional de la Task definido por F0-S5 que GitHub puede soportar
durante la revisión de un PR, sin ser propietario del lifecycle;
CANCELLED/CLOSED archivan con historia preservada. Rige la separación:

```text
Task Lifecycle
        ↓
GitHub supports it
```

y nunca `GitHub → defines Task Lifecycle`. Las herramientas no son
estados ni puertas: GitHub soporta el flujo, no lo define. La autoridad
de cada decisión proviene de las reglas y del modelo de gobernanza de la
Factory; GitHub aporta soporte, registro e integración.

## 3. Profundidad diferida a F4

La arquitectura detallada de Git/GitHub (convenciones de ramas, políticas
de protección, plantillas, flujos de release, permisos implementados)
queda diferida a F4. F0-S6 fija posición y dirección, no normativa
operativa.
