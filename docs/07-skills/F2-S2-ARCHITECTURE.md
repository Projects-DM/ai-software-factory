# F2-S2-ARCHITECTURE — Arquitectura y organización de Skills

Fase F2, Sprint F2-S2. Estado: ARCHITECTURE PROPOSED v0.1. Implementa
las 5 decisiones humanas aprobadas; fuente contractual: F2-S1 (no
duplicado). Sin Skills piloto, Agents, Runtime Adapter ni F2-S3.

## 1. Propósito

Habilitar la creación futura de Skills sin apropiarse de ella:
dónde viven, cómo se nombran, versionan, componen y descubren.

## 2. Alcance

Organización lógica/física, nomenclatura, versionado, composición,
dependencias, descubrimiento, fronteras Agent/Runtime/OpenCode,
Database Engineering como referencia. Fuera: Skills individuales,
Agents, adapter, enforcement.

## 3. Arquitectura lógica

`Capability → Skill → Technology realization`. General /
especializada / variante (perfil tecnológico, no Skill nueva) /
composición (cadena declarada, F2-S15).

## 4. Arquitectura física

```text
docs/07-skills/   # gobierno, arquitectura, contratos, validaciones F2
skills/           # instancias Factory-native
skills/INDEX.md   # catálogo de descubrimiento (no norma)
skills/<dominio>/SK-<DOMINIO>-<NNN>.md            # instancia del contrato
skills/<dominio>/SK-<DOMINIO>-<NNN>.validation.md # validación asociada
```

## 5. Estructura de directorios

Solo `skills/` + `INDEX.md` hoy. Dominios se crean con la primera
Skill real. Sin placeholders.

## 6. Nomenclatura

Archivo = ID (`SK-<DOMINIO>-<NNN>.md`); validación =
`<ID>.validation.md`. Sin `SKILL.md` normativo (`.opencode/skills/`
futuro = espejo generado del Runtime, nunca fuente).

## 7. Skill ID

`SK-<DOMINIO>-<NNN>`, inmutable tras aprobación; Name breve sin
jerga de producto/runtime; variante = perfil, no ID nuevo.

## 8. Relación Skill ↔ Contract

El archivo instancia los 18 campos F2-S1; el contrato vive en F2-S1
y no se copia.

## 9. Versionado

`vMAYOR.menor`: MAYOR = normativo/incompatible (+ supersession y
migración cuando aplique); menor = compatible. Trazabilidad:
versión + Changelog + Git + referencias.

## 10. Composición

`Requires`/`Provides` declarados (inputs/outputs del contrato);
cadenas en manifiestos F2-S15. `Composición ≠ Ejecución`;
`Dependencia ≠ Autorización`; `Capability ≠ Authorization`.

## 11. Dependencias

Declaradas y versionadas (ID+rango); grafo acíclico; sin circulares.

## 12. Requires / Provides

Requires: inputs/capacidades previas. Provides: outputs consumibles,
validables y trazables.

## 13. Descubrimiento

`skills/INDEX.md` (ID, Name, Capability, Version, Status, Domain).
Simple y evolutivo.

## 14. Catálogo

INDEX inicial vacío (tabla §arriba); se puebla con cada Skill
aprobada.

## 15. Capability → Skill → Technology

Tecnología fuera del contrato. Obligatorio: Database Engineering →
Relational Database Engineering → Skill → Technology Profile
(`Capability ≠ Technology`; `Skill ≠ Technology Profile`;
`Technology Profile ≠ Authorization`). Perfiles compatibles:
PostgreSQL, MySQL, MariaDB, SQL Server, Oracle y futuras
compatibles (conjunto abierto, no cerrado).

## 16. Agents

`Skill A ← Agent A/B/C` sin duplicar; ningún Agent es obligatorio
ni permanente; cambiar de Agent no redefine la Skill; la selección
es decisión de ejecución/gobernanza (capacidad, autorización,
contexto, disponibilidad, rendimiento, costo, compatibilidad,
confiabilidad, evidencia histórica), no propiedad estructural.
Sin identidad, rol, runtime ni herramienta del Agent en la Skill;
el uso vive en evidencia de ejecución. Nunca `Skill A → Agent A`
obligatorio.

## 17. Runtime

`Factory (Rules/Skills/Knowledge/State/Contracts/Evidence/
Validation/Governance/Workflow) → Agent Contract → Agent
Selection/Assignment → Agent A/B/C → Runtime Adapter → Selected
Runtime (OpenCode/Runtime B/Runtime C/futuro compatible) →
Tools`. Ningún Agent pertenece permanentemente a un Runtime.
`Agent ≠ Runtime`; `Runtime ≠ Model Provider`; `Model Provider ≠
Tool`. Proveedores (OpenAI, Anthropic, Google, Qwen u otros
compatibles) intercambiables por Agent/Runtime sin tocar el
contrato. Texto skill runtime-free.

## 18. Runtime Adapter

Frontera futura que traduce contrato↔runtime y autorización↔
permisos. Delimitado, no implementado.

## 19. OpenCode

Solamente uno de los runtimes potencialmente utilizables; puede
usarse como inicial, pero no es obligatorio, exclusivo ni
permanente. Nunca autoridad/fuente/propietario/dependencia
estructural. Sustituible sin modificar Rules, Skills, Contracts,
State, Knowledge, Evidence, Validation, Governance ni Workflow.
`.opencode/skills/<...>/SKILL.md` futuro = representación del
runtime (Factory → Adapter → `SKILL.md`, nunca al revés).

## 20. Factory-native / Runtime-specific

Normativo en `skills/`; específico en adapter/runtime. Nunca al revés.

## 20b. Regla de independencia transversal

Ningún Agent, Runtime, proveedor de modelos, herramienta o
tecnología concreta es obligatorio, exclusivo o permanente para la
Factory: todos son intercambiables detrás de sus fronteras. La
Skill declara capacidad/procedimiento/entradas/salidas/condiciones/
dependencias/evidencia/validación; la herramienta concreta es
medio de ejecución (salvo dependencia tecnológica declarada como
alcance deliberado).

## 21. Database Engineering

Capability → `SK-DB-NNN` tech-neutral → perfiles postgres/mysql/
mariadb/SQL Server/Oracle/futuro compatible. Representable hoy en
el modelo; nueva tecnología = nuevo perfil, no nueva capacidad.
Sin Skills por motor en este refinamiento.

## 22. Evolución

Versiones + INDEX + Git; sin reconstrucción para nuevas
tecnologías/runtimes.

## 23. Compatibilidad F1

Related Rules citadas; `RULE ≠ SKILL`; P09/P10/P12–P14/P18/P19.

## 24. Compatibilidad F2-00

Roadmap A–E, composición, gates y DB intactos.

## 25. Compatibilidad F2-S1

Contrato 18 campos íntegro; decisiones 1–5 aplicadas.

## 26. Límites de F2-S2

Sin Skills, Agents, adapter, enforcement, F2-S3.

## 27. Decisiones aprobadas

Raíz `skills/`; ID-archivo (no `SKILL.md`); `vMAYOR.menor`;
`INDEX.md` descubrimiento; sin piloto.

## 28. Changelog

v0.1 inicial (2026-10-04): arquitectura implementada según
decisiones 1–5.
v0.1-ref01 (2026-10-04): independencia transversal explícita
(§§15–17, 19–21, 20b); sin cambios de alcance ni componentes.
