# Zenith Lead Magnet Master

Sistema de agentes para Claude Code que crea **Lead Magnets epicos, interactivos y gamificados** (no PDFs de mierda) en espanol de Espana. Un lead magnet aqui no es informacion: es una **microtransformacion** que da resultado rapido, entretiene mientras sube el nivel de consciencia del lead, y deja claro que el "como completo" esta en tu oferta.

Creado por Joseph Moreno. Sintesis de formaciones de lead magnets + Big Idea (Bigadia) + niveles de consciencia (Schwartz) + biblia de copywriting (Cialdini, Bencivenga, Halbert, Sugarman, Hormozi, Brunson) + los principios raiz del copy: las 5 palancas de Blair Warren, headline (puñetazo) + subheadline (datos), y "vende el deseo, no la necesidad".

## Instalacion

**Opcion A · dentro de Claude Code** (recomendada · pegale esto a Claude):

```
/plugin marketplace add zenithmetodo/zenith-leadmagnet-master
/plugin install zenith-leadmagnet-master@zenith-leadmagnet-mp
```

**Opcion B · terminal (CLI):**

```bash
claude plugin marketplace add zenithmetodo/zenith-leadmagnet-master
claude plugin install zenith-leadmagnet-master@zenith-leadmagnet-mp
```

Luego **reinicia Claude Code**. Es gratis: puedes instalarlo y compartirlo con quien quieras.

## Como se usa

Slash creador (punto de entrada):

```
/zenith-leadmagnet-master:crear
```

Lanza el orquestador `lm-master`, que hace el discovery (pregunta TODO, incluido branding/colores/tipografia) y coordina 21 subagentes por compuertas, con validacion humana en cada gate.

## Pipeline por compuertas

`0 Discovery` -> `1 Spec` -> `2 Spec-Review` -> `3 Plan` -> `4 Idea+Naming` -> `5 Critica esceptica` -> `6 Creacion` -> `7 Propuesta HTML` -> `8 Gamificacion` -> `9 Intro cinematica` -> `10 Front (SVG/3D)` -> `11 Back` -> `12 Code-Review` -> `13 QA final`.

La propuesta de cada gate se da primero **en texto**; solo tras tu aprobacion se crea el **HTML y las carpetas**.

## Reglas innegociables

- Espanol de Espana.
- **CERO emojis. Todo icono es SVG.**
- El lead magnet transforma en minutos y entrega un "QUE grande", nunca el "como" completo.
- Gamificacion epica de verdad: intro cinematica antes de cargar la landing, mecanicas, SVGs animados; no un formulario que pasa de pregunta en pregunta.

## Subagentes

`lm-master`, `lm-spec-architect`, `lm-spec-reviewer`, `lm-plan-architect`, `lm-idea-naming`, `lm-critic`, `lm-creator`, `lm-copy-master`, `lm-gamification-architect`, `lm-intro-experience`, `lm-html-proposal`, `lm-frontend`, `lm-backend`, `lm-code-reviewer`, `lm-qa-auditor`, `lm-output-architect`, `lm-plugin-reviewer`, `lm-color-hierarchy`, `lm-visual-hierarchy`, `lm-scene-director`, `lm-scene-builder`.

## Conocimiento

Biblia de copywriting, Big Idea + clusters, fundamentos de lead magnet, los 5 pilares, niveles de consciencia, naming y promesa, biblia de gamificacion, biblia de SVG/FX, intro pre-landing, plantilla de presentacion. Ver `knowledge/00-INDEX.md`.

## Modelo

Todos los agentes corren en **Opus**. El contexto de 1M es un ajuste del harness (beta) que puedes activar en tu entorno.

## Licencia

MIT.
