---
description: "Meta-revisor del propio sistema/plugin: audita que todos los agentes tengan frontmatter correcto, llamadas correctas entre agentes, referencias de"
argument-hint: "[lo que necesitas]"
---

Usa el subagente **`lm-plugin-reviewer`** (herramienta Agent, `subagent_type: lm-plugin-reviewer`) para esta tarea.

Peticion del usuario:
$ARGUMENTS

Si `$ARGUMENTS` viene vacio, pregunta brevemente el contexto necesario (nicho, avatar, oferta, nivel de consciencia, branding: colores/tipografia) antes de lanzar el subagente `lm-plugin-reviewer`.
