# Intro cinematica pre-landing

Antes de cargar el lead magnet hay una **secuencia epica de entrada por nicho**. No se carga la landing directamente: primero hay una presentacion que crea expectativa. Regla: cero emojis, todo SVG, respeta prefers-reduced-motion, mobile-first, con skip accesible.

## Por que una intro
- Crea **expectativa** y sube el estatus percibido del lead magnet (no parece un formulario gratis).
- Ancla la **Big Idea** antes de que empiece a interactuar.
- Prepara emocionalmente (reptiliano): un pico de atencion antes de la primera pantalla.
- Da sensacion de producto cuidado = mas confianza = mas conversion.

## Patrones de intro (cuando usar cada uno)
1. **Cuenta atras animada:** un contador 3-2-1 en SVG que estalla en la marca. Para energia y arranque rapido.
2. **Loader tematico por nicho:** barra que se llena con micro-mensajes ("Analizando tu situacion...", "Preparando tu diagnostico..."). Crea anticipacion util.
3. **Bienvenida con el nombre apareciendo:** el nombre del lead magnet se dibuja/escribe. Para anclar naming.
4. **Secuencia de manifiesto:** 3-4 frases que aparecen una a una (la Big Idea en piezas). Para nivel de consciencia 1-2.
5. **Puerta/cortina que se abre (SVG):** metafora de "entras a algo". Para significado epico.
6. **Construccion de un grafico/mapa ante los ojos:** se dibuja el mapa del problema. Para nivel 2-3.
7. **Typewriter de una promesa:** la promesa se teclea sola. Para foco en una sola idea.
8. **Transicion 3D hacia la landing:** zoom/rotacion que "entra" en el lead magnet.

## Estructura temporal
- Total recomendado: **2,5 a 5 segundos** (corta; el pago emocional tiene que valer la espera).
- Skip siempre disponible ("Saltar intro", accesible por teclado).
- Auto-avance + opcion de tocar para entrar.
- Nunca bloquees mas de lo necesario: si el lead ya la vio (localStorage), acorta o salta.

## Personalizacion
- Por **nicho:** iconografia SVG, metafora y micro-mensajes propios del sector.
- Por **branding** (del discovery): colores primario/secundario, tipografia, tono.
- Por **fatia:** si conoces la fatia, el manifiesto cambia de angulo.

## Transicion epica a la landing
Fade + zoom + wipe con una mascara SVG, o un "barrido" de color que descubre la primera pantalla. Debe sentirse continua, no un corte brusco.

## Reglas
- Cero emojis, todo SVG.
- prefers-reduced-motion: version estatica equivalente (muestra el nombre + promesa sin animacion).
- Mobile-first, ligera, sin bloquear el render del contenido real (precarga la landing por detras).

## Mini esqueleto (contador + transicion)
```html
<div id="intro" class="intro" aria-label="Presentacion">
  <button class="skip" onclick="entrar()">Saltar intro</button>
  <svg class="count" viewBox="0 0 100 100"><text x="50" y="62" text-anchor="middle">3</text></svg>
</div>
<main id="lm" hidden><!-- lead magnet --></main>
```
```js
const n=document.querySelector('.count text');let c=3;
const t=setInterval(()=>{c--;if(c<=0){clearInterval(t);entrar();}else{n.textContent=c;}},800);
function entrar(){const i=document.getElementById('intro');i.classList.add('out');
  setTimeout(()=>{i.remove();document.getElementById('lm').hidden=false;},500);}
```
```css
.intro{position:fixed;inset:0;display:grid;place-items:center;background:var(--bg);transition:opacity .5s,transform .5s}
.intro.out{opacity:0;transform:scale(1.1);pointer-events:none}
@media (prefers-reduced-motion:reduce){.intro{transition:none}}
```
