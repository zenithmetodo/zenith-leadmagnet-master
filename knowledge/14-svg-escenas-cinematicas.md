# Biblia de escenas SVG cinematicas (nivel "locura")

Como construir escenas SVG animadas de altisimo nivel que se ven ANTES de la landing y por dentro del lead magnet. Cada nicho recibe una escena UNICA: nunca el mismo dibujo recauchutado. Cero emojis: todo SVG/canvas.

> AVISO DE NIVEL Y ORIGINALIDAD: el "aparato de laboratorio / destilador / botella con liquido" es SOLO un ejemplo prestado para fijar el lista de epicidad. NO lo uses como plantilla: repetirlo seria copiar a otro. La verdadera referencia es la VARIEDAD: hay que inventar mil dibujos distintos, uno por nicho, sin repetir nunca el mismo objeto ni la misma metafora. Cada escena es un dibujo nuevo (orbitas, ondas, constelaciones, motores, mapas, circuitos, cristales, tejidos, mareas, redes neuronales, lo que el nicho pida). El objetivo es arte generativo a medida que parezca de una pelicula o de un producto de lujo y haga decir "como han hecho esto". Si dudas entre algo correcto y algo espectacular, elige espectacular (siempre performante y accesible). El "liquido que fluye" es solo UNA tecnica entre muchas; usa la que mejor cuente ESE nicho.

## 1. Anatomia de una escena epica
Una escena que impacta combina 4 capas:
1. **Pieza central (line-art con vida):** un objeto del mundo dibujado a trazo fino (matraz, motor, reactor, reloj, cofre, circuito) que se ilumina y se mueve.
2. **Materia que fluye:** liquido, energia, datos o luz que viaja de un lado a otro. Es lo que hipnotiza.
3. **HUD de telemetria:** textos en mono con datos que cambian (TEMP, PRESION, VOLUMEN, PROTOCOLO, NIVEL, COORDENADAS), esquinas de la pantalla, color tenue. Da sensacion de "sistema en marcha".
4. **Stage-tracker:** una fila de etapas que se encienden en secuencia (CARGA - CALOR - VAPOR - CONDENSACION - COMPUESTO) y cuentan una micro-historia mientras carga.

## 2. Tecnicas clave (todas en SVG/CSS/JS)
- **Trazo que se dibuja:** `stroke-dasharray`/`stroke-dashoffset` animado para que el aparato "se construya" ante los ojos.
- **Liquido que sube (fill con ola):** un `<clipPath>` con la silueta del recipiente + un `<path>` de ola que se desplaza horizontalmente y sube su nivel. Dos olas desfasadas = liquido creible.
- **Gotas/particulas que viajan por un tubo:** define un `<path id="tubo">` (visible o invisible) y en JS usa `path.getPointAtLength(t)` para mover N gotas a lo largo del recorrido (el efecto "el liquido pasa de un lado a otro"). Alternativa CSS: `offset-path: path(...)` con `offset-distance` animado.
- **Flujo por el propio tubo:** segundo trazo encima del tubo con `stroke-dasharray` corto animando el offset = corriente que recorre la tuberia.
- **Glow / energia:** `filter` con `feGaussianBlur` + `feMerge`, o capas duplicadas con blur y `mix-blend-mode: screen`. Halo radial detras de la pieza con un `radialGradient`.
- **Burbujas / vapor:** particulas pequenas que ascienden con opacidad decreciente (canvas o SVG).
- **HUD counters:** numeros que suben/oscilan con `requestAnimationFrame` (TEMP 48 -> 52, VOL 000 -> 240 ML).
- **Temperatura de color:** la escena cambia de tono segun la "fase" (frio azul -> calor rojo/ambar), reforzando el progreso.
- **Parallax sutil:** capas que se mueven distinto con el puntero/scroll para dar profundidad.

## 3. Rendimiento y accesibilidad (obligatorio)
- Anima solo `transform`, `opacity`, `stroke-dashoffset`. Limita el numero de particulas (20-40). Usa `requestAnimationFrame`, no `setInterval` para motion fino.
- **prefers-reduced-motion:** ofrece una version estatica preciosa (la escena montada, sin flujo) con el mismo mensaje. Nunca dejes al usuario sin contenido.
- **Responsive:** todo en `viewBox` y unidades relativas; la escena se reescala sin romperse de 320 px a escritorio. HUD con `clamp()`.
- Skip accesible siempre. No bloquees el render del lead magnet (precargalo por detras).
- Cero emojis. Iconos y simbolos en path.

## 4. Estructura temporal (storytelling de carga)
La escena cuenta una micro-historia en 4-7 s mientras "prepara" el lead magnet:
1. Se dibuja el aparato (1 s).
2. Entra la materia y empieza a fluir (1-2 s).
3. El stage-tracker enciende etapa a etapa (2-3 s) con micro-mensajes.
4. "Compuesto listo" / clic -> transicion epica a la landing/test.

## 5. Mapa de metaforas por nicho (cada uno UNICO)
La pieza central es una metafora del problema/transformacion del avatar. Elige y PERSONALIZA, no copies:
- **Salud / hormonal / sueno:** laboratorio nocturno, alambique/destilador, viales que se equilibran, "quimica de tu noche".
- **Finanzas / dinero:** motor o reactor que se carga, camara acorazada que se llena, surtidor/medidores subiendo, tuberia de capital.
- **Productividad / foco:** linea de montaje, circuito que se enciende por tramos, bateria/condensador cargando, engranajes que sincronizan.
- **Fitness / cuerpo:** fragua que coge calor, horno metabolico, musculo como cable de alta tension, deposito de energia.
- **Captacion / agencias / negocio:** embudo real con leads como gotas, antena/radar que barre, panel de control con senales, tuberia de clientes.
- **Relaciones / pareja:** dos orbitas que se sincronizan, dos liquidos que se mezclan, dos senales que entran en fase.
- **Educacion / habilidades:** semilla a planta, mapa que se traza, constelacion que se conecta, llave que encaja en una cerradura.
Regla: el HUD y el stage-tracker se renombran al nicho (no "DESTILACION" para finanzas). El color, la metafora y las etapas se derivan del discovery (branding + dolor + transformacion).

## 6. Como encaja en el pipeline
- `lm-scene-director` decide la metafora UNICA del nicho, el guion de la escena, las etapas del stage-tracker, los textos del HUD y el momento epico.
- `lm-scene-builder` la construye en SVG+CSS+JS (flujo de liquido/energia, HUD, glow, transicion), performante, responsive, reduced-motion, cero emojis.
- Se usa en el Gate 9 (intro pre-landing) y puede reaparecer dentro del front (Gate 10) como "construyendo tu resultado".

## 7. Mini patron: gotas viajando por un tubo (referencia)
```html
<svg viewBox="0 0 400 300"><path id="tubo" d="M120 250 C 120 120, 280 180, 280 70" fill="none" stroke="#3a3a3a"/>
  <g id="gotas"></g></svg>
```
```js
const tubo=document.getElementById('tubo'),L=tubo.getTotalLength(),g=document.getElementById('gotas');
const N=14, gotas=[];
for(let k=0;k<N;k++){const c=document.createElementNS('http://www.w3.org/2000/svg','circle');
  c.setAttribute('r',3);c.setAttribute('fill','#ff5a36');g.appendChild(c);gotas.push({el:c,t:k/N});}
function tick(){gotas.forEach(o=>{o.t=(o.t+0.0025)%1;const p=tubo.getPointAtLength(o.t*L);
  o.el.setAttribute('cx',p.x);o.el.setAttribute('cy',p.y);o.el.setAttribute('opacity',0.3+0.7*Math.sin(o.t*Math.PI));});
  requestAnimationFrame(tick);}
if(!matchMedia('(prefers-reduced-motion: reduce)').matches)tick();
```
