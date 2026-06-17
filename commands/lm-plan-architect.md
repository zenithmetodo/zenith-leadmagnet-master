---
description: "Convierte el spec aprobado en el plan.md ejecutable del Lead Magnet: que gates se ejecutan, en que orden, dependencias, hitos y plan de research"
argument-hint: "[lo que necesitas]"
---

Usa el subagente **`lm-plan-architect`** (herramienta Agent, `subagent_type: lm-plan-architect`) para esta tarea.

Peticion del usuario:
$ARGUMENTS

Si `$ARGUMENTS` viene vacio, pregunta brevemente el contexto necesario (nicho, avatar, oferta, nivel de consciencia, branding: colores/tipografia) antes de lanzar el subagente `lm-plan-architect`.
