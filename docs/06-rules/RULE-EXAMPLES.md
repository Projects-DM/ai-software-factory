# RULE-EXAMPLES — F1-S1 Ejemplos mínimos del contrato

Fase: F1 — Rules. Sprint: F1-S1. Estado: ILUSTRATIVO.
Estos ejemplos solo demuestran que el contrato funciona. IDs con
prefijo `X-`: NO son Rules oficiales ni anticipan F1-S2…F1-S12. Ningún
ejemplo obliga ni autoriza nada.

## X-001 — MUST (formato mínimo completo)

- ID/Estado/Versión: X-001, PROPOSED, v0.1. Categoría: RC-01.
- Obligatoriedad/Severidad: MUST / HIGH.
- Condición: la Task produce un cambio.
- Acción: vincular cada cambio a su Task ID antes de avanzar.
- Restricción: ningún cambio huérfano avanza a TESTING.
- Autoridad: rol responsable del ámbito. Evidencia: vínculo Task↔diff
  (WHAT/WHEN/WHO/WHY/RESULT/SOURCE) al avanzar de estado.

## X-002 — MUST NOT

- ID: X-002. Categoría: RC-06. Obligatoriedad: MUST NOT. Severidad:
  CRITICAL. Condición: siempre, en todo alcance.
- Restricción: almacenar secretos en Git, docs, prompts, logs o
  evidencias sin protección. Acción: ninguna (prohibición pura).
- Violación: STOP + evidencia + escalado. Excepción: solo temporal,
  C05+, con revisión fechada.

## X-003 — SHOULD

- ID: X-003. Categoría: RC-02. SHOULD / MEDIUM. Condición: la
  asignación dispone de contexto amplio.
- Acción: reducir al contexto mínimo necesario documentando el recorte.
- Desviación admitida con justificación registrada; nunca silenciosa.

## X-004 — MAY

- ID: X-004. Categoría: RC-09. MAY / LOW. Condición: existe lección
  reutilizable validada. Acción: proponerla como candidata a Skill
  (sin crearla aquí). Sin evidencia de cumplimiento obligatoria.

## X-005 — HUMAN APPROVAL

- ID: X-005. Categoría: RC-08. HUMAN APPROVAL / HIGH. Condición:
  acción irreversible o fuera de límites delegados.
- Acción: solicitar decisión humana y esperar WAITING_HUMAN.
- Autoridad: decisor humano competente. Evidencia: aprobación
  vinculada (quién/qué/cuándo/alcance). Sin aprobación no hay avance.

## X-006 — Con excepción

- X-002 invocada con excepción E-X-002-1: Motivo (rotación de
  credencial en ventana controlada), Condición, Alcance (repo X, rama
  Y), Autoridad C05, Duración (expira 2026-10-05), Riesgo acotado,
  Evidencia de uso y Revisión a expiración. Expirada: la prohibición
  rige íntegra de nuevo.

## X-007 — Con dependencia

- ID: X-007. Categoría: RC-10. MUST / HIGH. Depende de: X-001
  (vínculo Task↔cambio) y principio P13. Condición: la Task solicita
  cierre. Acción: cerrar solo con traza completa verificada. Sin
  X-001 ACTIVE la dependencia se declara y fuerza revisión.

## X-008 — Con evidencia

- ID: X-008. Categoría: RC-04. MUST / HIGH. Evidencia al avanzar
  IMPLEMENTED→TESTING: WHAT test report, WHEN timestamp, WHO
  ejecutor, WHY criterios X-criterios, RESULT PASS/FAIL, SOURCE
  herramienta. Demuestra: Rule activa y aplicable, condiciones
  conocidas, decisión, autoridad y resultado.

## X-009 — Relación general/específica

- X-009-general (RC-03, MUST): todo cambio evalúa regresión.
- X-009-específica (RC-03, MUST): en cambios de configuración, la
  evaluación incluye despliegue en entorno equivalente y exige
  evidencia de reversión disponible. Especializa sin eliminar la
  restricción general; ante colisión, precede la específica (igual
  autoridad).
