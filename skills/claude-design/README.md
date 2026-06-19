# claude-design

Una skill de Claude Code que genera páginas web Astro+React+Tailwind+Motion completas a partir de un brief, descubriendo galerías de componentes en tiempo real.

**Versión**: 1.0.0
**Stack producido**: Astro 4 + React 18 + Tailwind 3 + Motion 11
**Velocidad de salida**: HTML-like (Lighthouse mobile ~95+)
**Velocidad de generación**: 5–15 minutos por página (live research)

---

## Qué hace

Cuando la invocas con un brief (cualquier nivel de detalle, desde "una landing pa mi curso de yoga" hasta un PDF de 50 páginas con avatar/oferta/secciones), la skill:

1. **Lee tu brief** y clarifica si falta algo crítico (max 2-3 preguntas batched).
2. **Compromete una dirección estética bold** y la presenta para que la apruebes.
3. **Investiga en tiempo real** las mejores galerías de componentes (shadcn, Magic UI, Aceternity, Motion-Primitives, lo que sea trending) vía WebSearch.
4. **Caza componentes** específicos (hero, features, pricing, etc.), comparando 2-3 candidatos por categoría.
5. **Compone** un proyecto Astro completo con Tailwind config + design tokens + componentes traducidos al stack consistente.
6. **Audita** mobile-friendliness, performance budget, y accesibilidad WCAG AA antes de entregar.
7. **Te entrega** una carpeta lista para `npm install && npm run dev`.

No memoriza URLs de componentes. Nunca caduca. Internet requerido.

---

## Cómo invocarla

### Opción 1 — Slash command explícito

```
/claude-design landing para mi curso de yoga, audiencia mujeres 30-50, tono cercano
```

### Opción 2 — Trigger phrase natural

Escribe cualquiera de estos en una conversación normal y se autoactiva:

- "haz una landing para X"
- "crea una página web de Y"
- "diseña un sitio para Z"
- "preciso una página para [W]"
- "build a landing page for X"
- "create a website for Y"

### Opción 3 — Auditar páginas existentes

```
/audit ./mi-pagina.html
/audit ./proyecto-astro/
/audit https://misitio.com
```

Aplica los mismos checks (mobile, performance, a11y) sobre páginas que ya tengas hechas. Útil para refactorizar.

---

## Qué obtienes

Una carpeta nueva en tu directorio actual con:

```
tu-proyecto/
  package.json          # Astro + React + Tailwind + Motion
  astro.config.mjs      # Configuración optimizada
  tailwind.config.js    # Tokens de paleta y fuentes elegidos
  tsconfig.json
  README.md             # Cómo correrlo
  src/
    layouts/Base.astro  # Layout con SEO, viewport, skip link
    pages/index.astro   # (y más rutas si es multipágina)
    components/         # Componentes fetchados y traducidos
    styles/globals.css  # Design tokens + reduced-motion canónico
```

Para correrlo:

```bash
cd tu-proyecto
npm install
npm run dev
# Abre http://localhost:4321
```

Para deployar:

```bash
npm run build
# Sube ./dist/ a Vercel/Netlify (drag-and-drop) o conecta el repo
```

---

## Garantías técnicas

| Garantía | Cómo se asegura |
|---|---|
| **Mobile-first** | Touch targets ≥44px, viewport meta, fluid type con clamp(), no overflow-x |
| **WCAG AA** | Contraste calculado, alt en imágenes, ARIA labels, focus visible, semantic HTML, skip link |
| **prefers-reduced-motion** | Bloque canónico en globals.css + inline en Base.astro como fallback |
| **Performance** | Astro islands (zero JS por defecto), bundle target <100KB, fonts con display:swap |
| **Imágenes** | Astro `<Image>` auto convierte a WebP/AVIF, lazy loading below-fold |

Lighthouse mobile estimado: 90-100 (depende del hosting + imágenes que añadas).

---

## Iteración rápida

Después de generar, si algo no te convence:

```
"el hero no me convence"
"cambia el footer"
"el color rojo es muy fuerte"
```

La skill recuerda los runners-up (segundas opciones) que evaluó durante la generación. Hace el swap en ~30 segundos sin re-investigar todo.

Para cambios drásticos ("cambia toda la dirección estética"): hace una regeneración parcial (mantiene tu brief, redo de Stages 2-7).

---

## Cómo compartir esta skill

La skill es **autocontenida** en `~/.claude/skills/claude-design/`. Para pasarla a otra persona:

```bash
# Comprime
cd ~/.claude/skills/
zip -r claude-design.zip claude-design/

# Envía claude-design.zip por email/WhatsApp/Drive
```

Quien la reciba:

```bash
# Descomprime en su misma carpeta
cd ~/.claude/skills/
unzip claude-design.zip

# Adicionalmente copia los slash commands
cp ~/.claude/skills/claude-design/.commands-source/* ~/.claude/commands/  # (ver nota abajo)
```

**Nota**: los slash commands `/claude-design` y `/audit` viven en `~/.claude/commands/`, NO dentro de la skill. Si compartes solo la skill, la otra persona puede invocarla con trigger phrases naturales pero no con slash commands hasta que también copie los `.md` de commands. Considera empacar ambos:

```bash
cd ~/.claude
zip -r claude-design-bundle.zip skills/claude-design/ commands/claude-design.md commands/audit-page.md
```

Quien la reciba:
```bash
cd ~/.claude
unzip claude-design-bundle.zip
```

Listo.

---

## Requisitos para quien la use

- ✅ Claude Code instalado
- ✅ Node.js 20+ (para correr el proyecto generado)
- ✅ Conexión a internet (para live research durante generación)
- ⚠️ Plugin `firecrawl` (opcional, mejora velocidad de fetch para sitios cerrados)

No requiere API keys, ni cuentas pagadas, ni MCPs propios.

---

## Estructura interna de la skill

Para tu yo del futuro o quien quiera modificarla:

```
~/.claude/skills/claude-design/
├── SKILL.md                      # Workflow principal, ~600 líneas
├── README.md                     # Este archivo
└── resources/
    ├── search-heuristics.md      # Cómo y dónde buscar
    ├── aesthetic-directions.md   # 22 direcciones estéticas + meta-rules
    ├── audit-checklist.md        # Hard + soft checks para Stage 6
    └── astro-template/           # Starter project para clonar
        ├── package.json
        ├── astro.config.mjs
        ├── tailwind.config.js
        ├── tsconfig.json
        └── src/
            ├── layouts/Base.astro
            ├── pages/index.astro
            └── styles/globals.css
```

`SKILL.md` lee los archivos de `resources/` on-demand (no los carga todos al inicio — context economy).

---

## Filosofía

Esta skill se inspira en `frontend-design` de Anthropic (la que es solo 42 líneas de filosofía pura). El insight clave: el "magic" de buen diseño no está en código pre-hecho, está en cómo razona el modelo. Esta skill añade encima:

1. **Investigación en tiempo real** (vs catálogo bakeado)
2. **Compromiso a una dirección bold** (vs opciones tibias)
3. **Audit estático mandatorio** (vs "espero que esté bien")
4. **Stack opinionado** (Astro + React + Tailwind + Motion)
5. **Output portable** (un proyecto = una carpeta)

---

## Versionado

- **1.0.0** — versión inicial. Single skill + 3 resource files + Astro template + 2 slash commands.

Cambios mayores futuros (v2):
- Memoria cross-session de generaciones previas (anti-repetition de direcciones)
- Soporte para frameworks alternativos (Next.js, SvelteKit)
- Auto-deploy a Vercel/Netlify integrado
- Generación de copy con neurocopy patterns

---

## Bugs conocidos / limitaciones v1

- ⚠️ Si `WebSearch` retorna spam, la calidad del output sufre. La skill tiene fallback a librerías conocidas pero idealmente no se activa.
- ⚠️ La generación es lenta (5-15 min) por la live research. Aceptado tradeoff vs catálogo bakeado.
- ⚠️ No soporta web apps con auth/state complejo. Solo landings y multipage estáticos.
- ⚠️ Audit estático correlaciona ~85% con Lighthouse real. Para 100% real, corre Lighthouse manualmente post-build.

---

## Créditos

Construida por Pedro Núñez en colaboración con Claude (Anthropic).

Inspirada en:
- `frontend-design` skill de Anthropic
- `web-architect-supreme` (el WAS anterior, predecesor con vanilla HTML)
- shadcn/ui (modelo de copy-paste)
- Astro + React island architecture
- Stripe Press / Vercel design philosophy
