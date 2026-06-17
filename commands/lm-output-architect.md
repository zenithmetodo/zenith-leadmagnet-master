---
description: "Convierte la salida de cada agente en dos archivos (.md legible + .html estetico print-to-PDF) y mantiene la estructura de carpetas del proyecto"
argument-hint: "[lo que necesitas]"
---

Usa el subagente **`lm-output-architect`** (herramienta Agent, `subagent_type: lm-output-architect`) para esta tarea.

Peticion del usuario:
$ARGUMENTS

Si `$ARGUMENTS` viene vacio, pregunta brevemente el contexto necesario (nicho, avatar, oferta, nivel de consciencia, branding: colores/tipografia) antes de lanzar el subagente `lm-output-architect`.
