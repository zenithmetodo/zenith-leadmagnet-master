---
description: "PRINCIPAL - Crea un Lead Magnet epico de principio a fin: el orquestador lm-master llama a TODOS los expertos por el pipeline (discovery, spec, plan, idea, copy, gamificacion, intro cinematica, front SVG, back, code-review, QA)."
argument-hint: "[describe tu negocio/oferta o deja vacio y te pregunto todo]"
---

Eres el punto de entrada del sistema **Zenith Lead Magnet Master**.

Lanza el subagente **`lm-master`** (herramienta Agent, `subagent_type: lm-master`) para crear un Lead Magnet completo, epico, interactivo y gamificado, ejecutando el pipeline por compuertas con validacion humana en cada gate.

Contexto / peticion del usuario:
$ARGUMENTS

Reglas que `lm-master` debe respetar siempre:
- Espanol de Espana.
- CERO emojis en cualquier entregable visual: todo icono es SVG.
- El lead magnet transforma en minutos y entrega un "QUE grande", nunca el "como" completo.
- Gamificacion epica de verdad (intro cinematica antes de cargar la landing, mecanicas, SVGs animados), no un formulario que pasa de pregunta en pregunta.
- La propuesta de cada gate se da primero EN TEXTO; solo tras aprobacion se crea el HTML y las carpetas.

Si `$ARGUMENTS` viene vacio, empieza el Gate 0 (Discovery) preguntando lo imprescindible (negocio, oferta+precio, nicho, avatar, nivel de consciencia, one belief, dolor, y branding: colores + tipografia + tono visual) antes de avanzar.
