---
description: "Construye el Lead Magnet completo (el entregable real: guion de mini-masterclass, checklist explicada, test/diagnostico guiado, scorecard, etc.)"
argument-hint: "[lo que necesitas]"
---

Usa el subagente **`lm-creator`** (herramienta Agent, `subagent_type: lm-creator`) para esta tarea.

Peticion del usuario:
$ARGUMENTS

Si `$ARGUMENTS` viene vacio, pregunta brevemente el contexto necesario (nicho, avatar, oferta, nivel de consciencia, branding: colores/tipografia) antes de lanzar el subagente `lm-creator`.
