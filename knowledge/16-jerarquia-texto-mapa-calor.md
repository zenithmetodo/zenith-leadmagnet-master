# Jerarquia de texto y mapa de calor de atencion

Como ordenar el texto y la composicion para que el ojo vaya, en el orden correcto, a lo que importa. El especialista usa esto para que cada pantalla del lead magnet tenga UN foco y se lea sola. Cero emojis.

## 1. Jerarquia tipografica
Cada pantalla tiene niveles claros, no "todo del mismo tamano":
- **Display / heroe:** la Big Idea, el resultado, el dato clave. Grande, con caracter (serif display o peso alto), contraste maximo.
- **H2 / subtitulo:** orienta y da contexto.
- **Cuerpo:** legible, 16-18 px equivalentes, linea de 45-75 caracteres.
- **Caption / meta:** datos secundarios, etiquetas, legales. Pequeno y atenuado.
Palancas de jerarquia: TAMANO, PESO, CONTRASTE (color/opacidad), ESPACIO alrededor, y POSICION. Con 3-4 niveles basta; mas niveles = ruido.

## 2. Escala y ritmo
- Usa una escala tipografica coherente (p. ej. 1.25 o 1.333 entre niveles) con `clamp()` para que sea fluida y responsive.
- Espaciado vertical ritmico (multiplos de una unidad base). El espacio en blanco NO es vacio: agrupa, separa y crea jerarquia.
- Interlineado mayor en cuerpo (1.5-1.6), menor en titulares (1.05-1.2).

## 3. Patrones de lectura (como escanea el ojo)
- **Patron F:** en pantallas con mucho texto, el ojo baja por la izquierda y barre arriba. Pon lo clave arriba e izquierda.
- **Patron Z:** en pantallas visuales/landing, recorre en zigzag de arriba-izq a abajo-der; coloca logo/promesa arriba, CTA al final del recorrido.
- **Layer cake:** si hay buenos titulares, el ojo salta de titular en titular; cada uno debe tener sentido suelto.
- La gente NO lee, escanea. Escribe para ser escaneado: titulares con significado, bullets, negritas con criterio.

## 4. Mapa de calor de atencion (que es y como se usa)
Un mapa de calor predice DONDE mira la gente y en que orden. Lo que mas "calienta" la atencion:
- TAMANO (lo grande gana).
- CONTRASTE (lo que rompe con su entorno).
- COLOR DE ACCION (ver jerarquia del color: ese 10 por ciento).
- AISLAMIENTO / espacio en blanco alrededor (un elemento solo destaca).
- CARAS y MIRADAS (atraen; y la mirada de una cara dirige a donde mira).
- MOVIMIENTO (lo animado capta primero).
- DIRECCION (flechas, lineas, la propia mirada apuntan al siguiente foco).
- POSICION (arriba y centro pesan mas al cargar).

Metodo del especialista (heatmap mental, sin herramienta externa):
1. Lista los elementos de la pantalla.
2. Asigna a cada uno un "peso de atencion" 0-10 segun los factores de arriba.
3. Comprueba que el elemento MAS importante (la Big Idea, el resultado, el CTA) es el mas caliente y que el orden de calor coincide con el orden en que quieres que lo lean.
4. Si algo secundario esta robando calor, baja su tamano/contraste o dale aire al heroe.

## 5. Reglas de oro
- **UN foco por pantalla.** Si compiten dos, no hay foco.
- **Revelacion progresiva:** muestra lo justo en cada paso (clave en lead magnets gamificados).
- **El CTA siempre en zona caliente** y con el color de accion, sin rivales cerca.
- **Contraste para guiar, no para gritar:** sube el del heroe, baja el del resto.

## 6. Tests rapidos de validacion
- **Squint test:** entorna los ojos; lo que sigue destacando es lo que domina. Debe ser lo importante.
- **Test de 5 segundos:** ensena la pantalla 5 s; si no captan la idea principal y el siguiente paso, la jerarquia falla.
- **Primer vistazo:** la primera cosa que ve, ¿es la que quieres?

## 6 bis. Cero solapamientos (collision-free) - REGLA DURA
NADA tapa a NADA. Ningun elemento puede solaparse, cubrir ni pisar a otro en NINGUN tamano de pantalla. Errores tipicos a evitar: un boton/CTA encima del stage-tracker o de un texto, el HUD de las esquinas pisando el titulo central en movil, un modal tapando el contenido sin overlay, texto que sale de su tarjeta, elementos fijos (sticky/fixed) montados unos sobre otros al fondo.
Como garantizarlo:
- Reserva ESPACIO real para cada elemento (usa flujo normal, flex/grid con gap, o contenedores apilados como un "dock" al fondo), no superpongas bloques fijos al azar.
- Define z-index solo cuando hay capas intencionadas (escena de fondo vs HUD vs contenido), y aun asi sin colisiones de contenido legible.
- Respeta `safe-area-inset-*` para que nada quede bajo notch/barra.
- PRUEBA en 320 px, 375 px, 768 px y escritorio: si dos cosas se tocan o se montan, esta mal.
- En escenas animadas: HUD, stage-tracker y CTA van en zonas separadas y reservadas; el dibujo de fondo no invade el texto.
Si dudas, deja mas aire. Un solo solapamiento basta para que parezca roto.

## 7. Checklist por pantalla
- [ ] 3-4 niveles tipograficos claros, no mas.
- [ ] UN heroe / UN foco.
- [ ] El mapa de calor pone lo caliente en lo importante (idea/resultado/CTA).
- [ ] Linea de 45-75 caracteres en cuerpo.
- [ ] Espacio en blanco usado para agrupar y jerarquizar.
- [ ] Pasa el squint test y el de 5 segundos.
- [ ] CERO solapamientos: nada tapa a nada en 320/375/768/escritorio (HUD, tracker, CTA, modales, tarjetas).
