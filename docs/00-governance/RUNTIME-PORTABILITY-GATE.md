# RUNTIME-PORTABILITY-GATE — Criterios de portabilidad para F2/F3

Gate de entrada: F2/F3 solo construyen Skills/Agents portables si
cumplen estos criterios. Verificación humana antes de implementar.

## Criterios

1. G-01: formato Factory-native de Skill definido; `SKILL.md` solo
   tras adapter. (Cierra R2.)
2. G-02: Agent Contract separado de parámetros runtime-specific.
3. G-03: mapeo Authorization → Permission documentado; ninguna config
   OpenCode como autoridad normativa.
4. G-04: estado normativo fuera de memoria de sesión; checklist de
   cierre de sesión exigible. (Cierra R1/R3.)
5. G-05: RP-TEST-001 ejecutable en diseño (ejecución cuando haya
   estado persistido).
6. G-06: 0 nuevas dependencias D2/D3 introducidas por F2/F3
   (re-auditar matriz RP-001…RP-010).

## Decisión

```text
6/6 PASS → CONTINUE F2 (mantener REC-01…REC-05 como requisitos de diseño)
≤5/6 → MINOR CHANGES → CORRECT → REVALIDATE (no implementa F2/F3 hasta cerrar)
D2/D3 nuevo → ARCHITECTURAL CHANGES → ADR/GOVERNANCE → CORRECT → REVALIDATE
```

Estado actual (pre-F2): matriz D0 ×5 / D1 ×5, 0 bloqueantes →
auditoría favorable a continuar con guardarraíles; el gate se evalúa
al diseñar F2, no hoy.
