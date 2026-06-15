# Biblia de SVG y efectos visuales

## REGLA MAESTRA
CERO emojis, NUNCA, en ningun entregable que vea el lead. Toda iconografia, ilustracion, estado y celebracion se hace con **SVG** (o canvas para particulas). Un emoji en el front es motivo de corte del pipeline.

## Por que SVG
Escalable (nitido en cualquier pantalla), animable (CSS/JS), accesible (titulo/desc/ARIA), ligero, estilable con `currentColor` para heredar el tema del branding.

Estructura base de un SVG:
```html
<svg viewBox="0 0 24 24" role="img" aria-label="Verificado" fill="none" stroke="currentColor" stroke-width="2">
  <title>Verificado</title>
  <path d="M20 6 9 17l-5-5"/>
</svg>
```

## Patrones de SVG animado
- **Trazo que se dibuja:** `stroke-dasharray` + `stroke-dashoffset` animado (checks, lineas, graficos).
```css
.draw{stroke-dasharray:100;stroke-dashoffset:100;animation:draw .6s ease forwards}
@keyframes draw{to{stroke-dashoffset:0}}
```
- **Pulsos / latidos:** `transform: scale()` con `transform-origin:center`.
- **Rotaciones / loaders:** rotacion infinita en un grupo `<g>`.
- **Gradientes animados:** `linearGradient` con stops animados.
- **Particulas / confetti:** canvas 2D (no emoji).
- **Iconos de estado:** check, alerta, candado, flecha, estrella, todos en path.

## Microinteracciones
- Hover/focus/active con transiciones suaves.
- Curvas: `cubic-bezier(.2,.8,.2,1)` para entradas; springs para feedback.
- Feedback al tocar: cambio de color + micro-escala (95-105 por ciento).

## Efectos 3D ligeros con CSS
- `perspective` en el contenedor, `rotateX/rotateY` en la tarjeta.
- Parallax por scroll o por movimiento del puntero (capas con `translateZ`).
- Tilt en tarjetas (seguir el cursor con limites suaves).
```css
.escena{perspective:900px}
.carta{transform:rotateY(8deg) rotateX(4deg);transition:transform .2s}
```

## Rendimiento
- Anima solo `transform` y `opacity` (evita layout thrashing).
- `will-change` con cuidado (solo en lo que se anima).
- Carga diferida de assets pesados.
- **prefers-reduced-motion:** respeta siempre la preferencia de accesibilidad.
```css
@media (prefers-reduced-motion: reduce){*{animation:none!important;transition:none!important}}
```

## Mobile-first
- Areas tactiles minimas comodas, `viewport` correcto, `env(safe-area-inset-*)`.
- Gestos: swipe para avanzar; evita hover como unico estado.

## Accesibilidad
- Roles ARIA, foco visible, contraste suficiente.
- `<title>`/`<desc>` en SVG informativos; `aria-hidden` en los decorativos.
- No depender solo del color para transmitir estado.

## Mini kit reutilizable
```html
<!-- Barra de progreso accesible -->
<div class="prog" role="progressbar" aria-valuemin="0" aria-valuemax="100" aria-valuenow="40">
  <span style="width:40%"></span>
</div>
```
```css
.prog{height:10px;background:#1c2030;border-radius:99px;overflow:hidden}
.prog span{display:block;height:100%;background:linear-gradient(90deg,var(--acc),var(--acc2));transition:width .5s cubic-bezier(.2,.8,.2,1)}
```
