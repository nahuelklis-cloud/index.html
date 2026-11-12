# Documentación técnica completa — Sitio web E.E.S.T. N.º 2

Esta documentación explica la construcción de la página institucional, el propósito de sus archivos y el funcionamiento de las etiquetas, atributos, clases, variables, selectores, propiedades, funciones y APIs empleadas.

## 1. Estructura del proyecto

| Archivo | Función |
|---|---|
| `EESTN2.html` | Define la estructura, el contenido y la semántica de la página. |
| `organigrama.html` | Página independiente preparada para mostrar el PNG del organigrama institucional. |
| `styles.css` | Controla colores, tipografías, posiciones, animaciones y adaptación a diferentes pantallas. |
| `script.js` | Agrega interactividad: menú móvil, animaciones, pestañas, acordeones, ventana de especialidades y formulario. |
| `Escudo.png` | Escudo oficial empleado como identidad visual en el encabezado y pie. |
| Los dos archivos `.pdf` | Documentos utilizados como fuente para definir contenido y requisitos. No son cargados por la página. |

La separación entre HTML, CSS y JavaScript permite modificar contenido, apariencia y comportamiento de manera independiente.

---

# 2. HTML: estructura y contenido

## 2.1 Declaración inicial y elemento raíz

### `<!doctype html>`

Indica al navegador que el documento utiliza HTML5. No es una etiqueta visible; activa el modo de estándares modernos y evita interpretaciones antiguas del diseño.

### `<html lang="es">`

Es el elemento raíz que contiene toda la página.

- `lang="es"` informa que el idioma principal es español.
- Ayuda a lectores de pantalla, traductores automáticos y buscadores.

## 2.2 Metadatos de `<head>`

### `<head>`

Contiene información técnica que no forma parte directa del contenido visible.

### `<meta charset="utf-8">`

Define UTF-8 como codificación. Permite mostrar correctamente caracteres como `ñ`, tildes, `.º`, flechas y símbolos.

### `<meta name="viewport" content="width=device-width,initial-scale=1">`

Configura la visualización móvil:

- `width=device-width`: el ancho lógico coincide con el ancho real del dispositivo.
- `initial-scale=1`: evita un zoom inicial artificial.

Sin esta etiqueta, el sitio se vería reducido en teléfonos.

### `<meta name="description" ...>`

Proporciona una descripción breve para buscadores, vistas previas y herramientas de indexación.

### `<title>`

Define el texto de la pestaña del navegador: `E.E.S.T. N.º 2 | Valentín Alsina`.

### `<link rel="preconnect">`

Solicita al navegador iniciar anticipadamente la conexión con Google Fonts. Esto reduce la demora de carga de las tipografías.

- `rel="preconnect"` describe el tipo de optimización.
- `href` contiene el servidor de destino.
- `crossorigin` permite la conexión con recursos servidos desde otro dominio.

### `<link href="...fonts.googleapis.com..." rel="stylesheet">`

Importa las familias tipográficas:

- **DM Sans** para textos, botones y párrafos.
- **Space Grotesk** para títulos y elementos destacados.
- Los valores `400`, `500`, `600` y `700` son distintos grosores.

### `<link rel="stylesheet" href="styles.css">`

Conecta el HTML con la hoja de estilos local.

## 2.3 Elementos generales del cuerpo

### `<body>`

Contiene todo lo que se presenta o ejecuta en la página.

### Enlace `.skip`

```html
<a class="skip" href="#main">Saltar al contenido</a>
```

Es un recurso de accesibilidad. Permite que una persona que navega con teclado salte el menú y llegue directamente al contenido. Normalmente queda fuera de pantalla y aparece al recibir foco.

### `<header>`

Representa el encabezado global. Se mantiene fijo durante el desplazamiento.

### `<nav class="nav wrap">`

Indica semánticamente que el contenido es navegación principal.

- `.nav` organiza logo, enlaces y botón móvil.
- `.wrap` limita el ancho y centra el contenido.

### Identidad `.brand`

Es un enlace hacia `#inicio` que agrupa:

- `<img src="Escudo.png">`: escudo oficial.
- `alt="Escudo oficial..."`: descripción para lectores de pantalla y alternativa si falla la imagen.
- `<strong>`: nombre principal.
- `<small>`: ubicación secundaria.

### Botón `.menu`

```html
<button class="menu" aria-label="Abrir menú" aria-expanded="false">☰</button>
```

- `<button>` se utiliza porque realiza una acción, no una navegación.
- `aria-label` da un nombre accesible al símbolo visual.
- `aria-expanded` comunica si el menú está abierto. JavaScript cambia su valor.
- `☰` es el icono textual de menú.

### Contenedor `.links`

Agrupa los vínculos principales. Los valores `href="#identificador"` conducen a secciones de la misma página, mientras que `href="organigrama.html"` abre el documento independiente del organigrama. `.top-cta` distingue visualmente la preinscripción como acción principal.

El vínculo **Organigrama** se creó como navegación entre documentos y no como un ancla interna. Por ese motivo no utiliza `#organigrama`: el contenido del organigrama fue retirado de `EESTN2.html` y se trasladó a una página preparada específicamente para él.

## 2.4 Contenido principal

### `<main id="main">`

Contiene el contenido central único del documento. El `id` es el destino del enlace “Saltar al contenido”.

### `<section>`

Se usa para dividir el contenido en bloques temáticos. Cada sección importante posee un `id` para ser alcanzada desde el menú:

| ID | Contenido |
|---|---|
| `inicio` | Presentación principal. |
| `escuela` | Identidad y valores. |
| `oferta` | Tecnicaturas. |
| `plan` | Ciclos de estudio. |
| `novedades` | Noticias escolares. |
| `tramites` | Accesos y documentación. |
| `requisitos` | Documentos para inscribirse. |
| `contacto` | Información y formulario. |

## 2.5 Sección principal `.hero`

`hero` es el término habitual para el bloque inicial de gran impacto.

- `.hero-grid` divide la sección en texto e ilustración.
- `.hero-copy` contiene el mensaje institucional.
- `.eyebrow` es el pequeño rótulo ubicado sobre un título.
- `<h1>` es el título más importante de la página. Solo se utiliza una vez.
- `<br>` fuerza un salto de línea visual.
- `<em>` permite aplicar un color especial a “convierten”. Aquí su función es visual, aunque semánticamente también indica énfasis.
- `.lead` identifica el párrafo introductorio.
- `.actions` agrupa los botones principales.
- `.btn`, `.yellow` y `.outline` permiten combinar estilo base y variantes.
- `.stats` contiene los tres datos resumidos.

La ilustración de código utiliza:

- `<pre>` para conservar espacios y saltos de línea.
- `<i>`, `<mark>` y `<u>` como fragmentos coloreables del código ficticio.
- `.chip`, `.c1`, `.c2` y `.c3` para las etiquetas flotantes.
- `.ticker` para la franja de palabras técnicas.

## 2.6 Encabezados reutilizables

La combinación `.heading`, `.eyebrow`, `.blue` y `.center` se reutiliza para conservar una jerarquía consistente.

- `<h2>` encabeza cada sección.
- `<h3>` nombra tarjetas o subsecciones.
- `.blue` convierte el rótulo en azul cuando el fondo es claro.
- `.center` centra el bloque y limita su ancho.

## 2.7 Valores institucionales

`.values` es una cuadrícula de elementos `<article>`. Se usa `<article>` porque cada tarjeta tiene sentido por sí misma.

- `.hot` señala la tarjeta destacada con fondo amarillo.
- `<i>` contiene el número decorativo.
- `<b>` contiene un símbolo visual.

## 2.8 Oferta académica

`.programs` contiene dos `.program`:

- `.cyan` aplica fondo celeste.
- `.gold` aplica fondo amarillo.
- `data-program` guarda el nombre de la especialidad para JavaScript.
- `<ul>` representa la lista de áreas de aprendizaje.
- El `<button>` abre una ventana con el perfil profesional.

Los atributos `data-*` permiten guardar datos personalizados válidos en HTML. En JavaScript, `data-program="Programación"` se consulta como `element.dataset.program`.

## 2.9 Plan y ciclos de estudio

`.tabs` funciona como selector entre ciclo básico y superior.

- `role="tablist"` comunica a tecnologías asistivas que agrupa pestañas.
- Cada `data-cycle` coincide con el `id` del panel correspondiente.
- `.active` decide qué botón y qué panel están visibles.
- `.cycle` es un panel inicialmente oculto.
- `<aside>` contiene información complementaria del ciclo.
- `.subjects` lista áreas y explicaciones.

## 2.10 Materias específicas y acordeón

El HTML contiene inicialmente solo:

```html
<div id="accordion"></div>
```

JavaScript genera su contenido según la orientación elegida.

- `.orient` agrupa los botones Programación e Informática.
- `data-orient="prog"` y `data-orient="info"` son claves que coinciden con el objeto `data` de JavaScript.
- `.acc` representa un año.
- `.acc-content` contiene su lista de materias.
- `.open` abre el bloque.
- `aria-expanded` expresa accesiblemente el estado.

## 2.11 Prácticas profesionalizantes

`.practice-grid` divide ilustración y explicación.

- `.practice-art` crea una pieza gráfica con CSS, sin necesitar una fotografía.
- `.practice-copy` contiene la explicación tomada de las consignas.
- `.points` enumera problemas reales, trabajo profesional y evaluación por capacidades.

## 2.12 Novedades

Cada noticia es un `<article>` con:

- `<time>` para representar una fecha.
- `<small>` para la categoría.
- `<h3>` para el título.
- Un enlace con flecha para la acción relacionada.

Las fechas funcionan como contenido demostrativo del diseño y deben actualizarse cuando la institución disponga de un calendario oficial.

## 2.13 Página independiente del organigrama

El organigrama ya no se encuentra como sección dentro de `EESTN2.html`. El menú principal redirige a `organigrama.html`, evitando cargar una imagen potencialmente grande dentro de la página institucional.

La nueva página conserva una estructura HTML completa y válida:

```html
<body class="organigrama-page">
  <main class="organigrama-shell">
    <div class="organigrama-box" id="organigrama-contenedor"></div>
    <a class="organigrama-back" href="EESTN2.html">
      ← Volver al sitio principal
    </a>
  </main>
</body>
```

### `<body class="organigrama-page">`

Aplica a toda la página el fondo azul marino, el centrado del contenido y una altura mínima igual a la pantalla.

### `<main class="organigrama-shell">`

Es el contenido principal de la página. Organiza verticalmente el contenedor de la imagen y el botón de regreso. Se utiliza `<main>` para mantener una estructura semántica y accesible aunque la página sea sencilla.

### `#organigrama-contenedor` y `.organigrama-box`

Es el espacio reservado para insertar posteriormente el PNG. El `id` permite localizarlo de forma inequívoca y la clase aplica su presentación visual. Mientras esté vacío, CSS muestra automáticamente el texto orientativo “Insertá aquí la imagen PNG del organigrama”. Ese texto no forma parte del HTML y desaparece en cuanto se agrega contenido.

La inserción prevista es:

```html
<div class="organigrama-box" id="organigrama-contenedor">
  <img
    src="organigrama.png"
    alt="Organigrama institucional de la E.E.S.T. N.º 2"
  >
</div>
```

El atributo `alt` debe describir la imagen. Si el organigrama contiene mucha información textual, conviene proporcionar además una transcripción accesible en otra página o mediante texto cercano.

### Enlace `.organigrama-back`

Funciona visualmente como botón, pero se implementa con `<a>` porque su acción es navegar hacia otro documento. `href="EESTN2.html"` regresa al sitio original. La flecha `←` refuerza visualmente la idea de volver.

## 2.14 Trámites y requisitos

- `.procedures` divide introducción y enlaces.
- `.procedure-list` agrupa accesos.
- `.requirements` destaca los tres documentos mencionados por la consigna.

No se inventaron URLs de formularios ni de boletines. Los enlaces llevan a contacto hasta que la escuela suministre destinos oficiales.

## 2.15 Formulario de contacto

### `<form id="form">`

Agrupa controles que conceptualmente se enviarían a la escuela. Actualmente es una demostración del lado del navegador y no posee servidor.

### `<label>`

Relaciona el texto descriptivo con el control contenido dentro de él. Esto amplía el área clicable y mejora la accesibilidad.

### `<input>`

- El input de nombre usa el tipo de texto predeterminado.
- `type="email"` solicita un correo y activa validación básica del navegador.
- `required` impide enviar el formulario vacío.
- `placeholder` muestra un ejemplo, pero no reemplaza al `<label>`.

### `<select>` y `<option>`

Crean la lista de motivos de consulta.

### `<textarea>`

Permite escribir un mensaje de varias líneas. `rows="3"` propone una altura inicial.

### `.wide`

Hace que el control ocupe las dos columnas del formulario.

### `.status` y `role="status"`

Recibe el mensaje de confirmación. `role="status"` permite que los lectores de pantalla anuncien el cambio sin mover el foco.

## 2.16 Pie y ventana modal

### `<footer>`

Contiene identidad, navegación secundaria, frase institucional y copyright.

### `<dialog>`

Es el elemento nativo de HTML para una ventana modal.

- `.close` es el botón de cierre.
- `#modal` recibe contenido dinámico.
- `dialog.showModal()` abre la ventana y activa su fondo modal.
- `dialog.close()` la cierra.

### `<script src="script.js">`

Se ubica al final para que el HTML ya exista cuando JavaScript busque sus elementos.

---

# 3. CSS: diseño y presentación

## 3.1 Variables de `:root`

`:root` representa el elemento raíz y permite declarar propiedades personalizadas reutilizables.

| Variable | Valor | Uso |
|---|---:|---|
| `--ink` | `#111a2d` | Texto oscuro principal. |
| `--navy` | `#101a32` | Fondos azul marino. |
| `--blue` | `#1748f5` | Azul eléctrico de acciones. |
| `--cyan` | `#55dce7` | Celeste de tarjetas y énfasis. |
| `--yellow` | `#ffdf59` | Amarillo de botones y destacados. |
| `--paper` | `#f3f1e9` | Fondo claro cálido. |
| `--line` | `#d5d5d2` | Bordes y separadores. |
| `--muted` | `#687080` | Texto secundario. |

Se leen con `var(--nombre)`. Centralizarlas permite cambiar toda la identidad cromática desde un solo lugar.

## 3.2 Selectores

- `*` selecciona todos los elementos.
- `elemento` selecciona por etiqueta, por ejemplo `body`.
- `.clase` selecciona por clase.
- `#id` selecciona un identificador único.
- `.padre .hijo` selecciona descendientes.
- `.padre>hijo` exige que sea hijo directo.
- `.clase:hover` actúa cuando el puntero pasa encima.
- `.clase:focus` actúa cuando el elemento recibe foco.
- `.clase::before` y `::after` crean pseudoelementos decorativos.
- `[data-cycle]` selecciona por presencia de atributo.
- `:not(...)` excluye coincidencias.
- `:last-child` selecciona el último hijo.

## 3.3 Reinicio y reglas generales

- `box-sizing:border-box` incluye padding y borde dentro del ancho declarado.
- `scroll-behavior:smooth` suaviza los enlaces internos.
- `margin:0` elimina márgenes predeterminados.
- `font:16px/1.6 ...` resume tamaño, interlineado y familia.
- `text-decoration:none` elimina el subrayado inicial de enlaces.
- `.wrap` usa `min()` para elegir el menor valor entre `1160px` y el ancho disponible menos márgenes.

## 3.4 Posicionamiento y capas

- `position:fixed` fija el encabezado respecto de la ventana.
- `position:relative` crea una referencia para hijos absolutos.
- `position:absolute` posiciona decoraciones dentro de esa referencia.
- `inset` resume `top`, `right`, `bottom` y `left`.
- `z-index` controla qué capa aparece delante.
- `overflow:hidden` recorta contenido que sobresale.

## 3.5 Encabezado y menú

- `header.scrolled` se agrega al desplazar la página y crea un fondo oscuro.
- `backdrop-filter:blur(...)` desenfoca lo que queda detrás.
- `.links` tiene fondo negro translúcido para que el texto sea legible sobre cualquier sección.
- `.links.open` aplica un fondo casi opaco en móviles.
- `!important` se utiliza en esa corrección puntual para garantizar que las reglas del menú abierto superen variantes anteriores.
- `isolation:isolate` crea un contexto de composición independiente.
- `text-shadow` refuerza el contraste del texto blanco.
- `.top-cta` conserva fondo amarillo y texto oscuro.

## 3.6 Flexbox y Grid

El sitio combina dos sistemas:

### Flexbox

Se usa cuando los elementos se organizan principalmente en una dimensión.

- `display:flex` activa el sistema.
- `align-items:center` alinea transversalmente.
- `justify-content:space-between` distribuye extremos.
- `gap` crea separación uniforme.
- `flex-direction:column` cambia a disposición vertical.
- `flex:1` permite ocupar el espacio restante.

### CSS Grid

Se usa para composiciones de filas y columnas.

- `display:grid` activa la cuadrícula.
- `grid-template-columns` define las columnas.
- `1fr` representa una fracción del espacio disponible.
- `.85fr 1.15fr` crea columnas proporcionales diferentes.
- `repeat(3,1fr)` crea tres columnas iguales.
- `grid-column:1/-1` extiende un elemento entre la primera y última línea.
- `place-items:center` centra en ambos ejes.

## 3.7 Tipografía

- `font-family` selecciona la familia.
- `font-weight` determina el grosor.
- `font-size:clamp(mínimo,preferido,máximo)` crea títulos fluidos.
- `line-height` controla el espacio vertical.
- `letter-spacing` ajusta el espaciado de letras.
- `text-transform:uppercase` convierte visualmente a mayúsculas.
- `font-style:normal` elimina la cursiva predeterminada de `<em>` o `<i>` cuando se usan como recurso visual.

## 3.8 Colores, bordes y sombras

- `background` define fondo sólido, imagen o degradado.
- `color` controla el texto.
- Los colores hexadecimales de ocho dígitos, como `#101a32ed`, incluyen transparencia.
- `rgba()` también expresa transparencia.
- `border` define grosor, estilo y color.
- `border-radius` redondea esquinas.
- `box-shadow` añade profundidad.
- `filter:drop-shadow()` crea una sombra siguiendo la silueta transparente del escudo.

## 3.9 Imágenes y escudo

`.brand>img` establece:

- `width` y `height` para reservar dimensiones estables.
- `object-fit:contain` para mostrar el escudo completo sin recortarlo ni deformarlo.
- `flex:0 0 auto` para impedir que Flexbox lo comprima.
- En el pie se aumenta a `68px` mediante `.footer .brand>img`.

## 3.10 Transformaciones, transiciones y animación de entrada

- `transform:rotate(-2deg)` inclina la tarjeta de código.
- `translateY()` desplaza elementos.
- `transition:.65s` interpola cambios suavemente.
- `.reveal` empieza transparente y desplazado.
- `.reveal.visible` vuelve a opacidad completa y posición natural.
- JavaScript agrega `.visible` cuando el elemento entra en pantalla.

## 3.11 Pseudoelementos

`.visual::before` y `.visual::after` dibujan círculos decorativos sin añadir HTML. Los marcadores de listas también se crean con `li::before` y la propiedad `content`.

## 3.12 Acordeón animado

`.acc-content` utiliza una cuadrícula con `grid-template-rows:0fr`. Al agregarse `.open`, cambia a `1fr`. El contenido interno tiene `overflow:hidden`, por lo que la transición produce apertura y cierre suaves sin calcular alturas con JavaScript.

## 3.13 Diseño responsive

Las reglas `@media(max-width:900px)` se aplican a tabletas y pantallas menores:

- Aparece el botón de menú.
- `.links` se convierte en panel fijo vertical.
- Las composiciones principales pasan a una columna.
- Departamentos y requisitos reducen columnas.

Las reglas `@media(max-width:640px)` optimizan teléfonos:

- Se reducen márgenes y espacios.
- Se ajusta el tamaño del título.
- Tarjetas y noticias quedan en una columna.
- El formulario pasa a una sola columna.
- Se ocultan elementos flotantes secundarios.

`@media(prefers-reduced-motion:reduce)` respeta la preferencia del sistema de personas sensibles al movimiento: elimina desplazamientos animados y el scroll suave.

## 3.14 Estilos de la página del organigrama

### `.organigrama-page`

- `min-height:100vh` hace que ocupe como mínimo toda la altura visible.
- `background:var(--navy)` reutiliza el azul marino institucional.
- `color:#fff` establece texto blanco como valor inicial.
- `display:grid` y `place-items:center` centran el contenido.
- `padding` evita que el contenido toque los bordes.

### `.organigrama-shell`

- `width:min(1160px,100%)` limita el ancho sin desbordar pantallas pequeñas.
- `display:flex` y `flex-direction:column` apilan el contenedor y el botón.
- `align-items:center` centra el contenedor.
- `gap:28px` crea separación entre ambos elementos.

### `.organigrama-box`

- `width:100%` utiliza todo el ancho disponible.
- `min-height:620px` reserva un área amplia antes de incorporar la imagen.
- El borde discontinuo celeste indica que se trata de un espacio pendiente.
- El fondo blanco casi transparente conserva la paleta oscura.
- `display:grid` y `place-items:center` centran la imagen o el mensaje provisional.
- `box-shadow` separa sutilmente el panel del fondo.

### `.organigrama-box:empty::before`

Combina dos conceptos:

- `:empty` selecciona el contenedor únicamente cuando no tiene ningún nodo hijo.
- `::before` crea el mensaje provisional mediante `content`.

Al insertar un `<img>`, el div deja de estar vacío y el mensaje desaparece automáticamente. Para que `:empty` funcione, no se deben dejar textos o espacios significativos dentro del div antes de la imagen.

### `.organigrama-box img`

- `max-width:100%` impide el desbordamiento horizontal.
- `height:auto` conserva la proporción original.
- `object-fit:contain` asegura que la imagen completa permanezca visible.
- `display:block` elimina el pequeño espacio inferior propio de imágenes en línea.

### `.organigrama-back`

Reutiliza el amarillo y azul marino del sitio. `align-self:flex-start` ubica el botón a la izquierda del contenedor. La transición suaviza el cambio de color y el desplazamiento de `-4px` al pasar el puntero.

En pantallas de hasta `640px`, se reduce el padding exterior y el contenedor pasa a una altura mínima del `70vh`, aprovechando mejor el espacio de los teléfonos.

### Selectores heredados del organigrama anterior

`styles.css` todavía conserva `.org`, `.chief`, `.departments` y `.role`. Estas reglas pertenecían a la primera versión, en la que el organigrama se dibujaba directamente dentro de `EESTN2.html`. Ya no tienen elementos coincidentes en el HTML principal y, por lo tanto, actualmente no producen ningún efecto visual. Se conservaron deliberadamente para poder reutilizarlas si el sitio externo evoluciona hacia un organigrama construido con HTML en lugar de una imagen PNG.

---

# 4. JavaScript: comportamiento

## 4.1 Selección de elementos

```js
document.querySelector('selector')
```

Devuelve el primer elemento que coincide con un selector CSS.

```js
document.querySelectorAll('selector')
```

Devuelve todos los elementos coincidentes en una `NodeList`, recorrida con `forEach()`.

Las constantes iniciales:

- `header`: encabezado fijo.
- `menu`: botón hamburguesa.
- `links`: panel de enlaces.

`const` declara una referencia que no se reasigna.

## 4.2 Evento de desplazamiento

```js
addEventListener('scroll', () =>
  header.classList.toggle('scrolled', scrollY > 20)
);
```

- `addEventListener` registra una función para un evento.
- `scrollY` contiene los píxeles desplazados verticalmente.
- `classList.toggle(clase, condición)` agrega la clase si la condición es verdadera y la elimina si es falsa.
- La función flecha `()=>{}` es una sintaxis compacta de función.

## 4.3 Menú móvil

Al hacer clic:

1. `links.classList.toggle('open')` abre o cierra el panel.
2. El resultado booleano se guarda en `open`.
3. `setAttribute('aria-expanded', open)` sincroniza el estado accesible.

Cada enlace recibe otro evento que elimina `.open` después de navegar.

## 4.4 `IntersectionObserver`

Observa si los elementos `.reveal` entran en la ventana visible.

- `entries` contiene los cambios observados.
- `entry.isIntersecting` indica si el elemento está visible.
- `entry.target` es el elemento concreto.
- `observer.unobserve()` deja de observar después de animarlo una vez.
- `{threshold:.12}` exige aproximadamente un 12 % visible antes de activar la animación.

Este método es más eficiente que comprobar posiciones continuamente durante el scroll.

## 4.5 Pestañas de ciclos

Para cada `[data-cycle]`:

1. Se quita `.active` de todos los botones.
2. Se ocultan todos los `.cycle`.
3. Se activa el botón pulsado.
4. `document.getElementById(b.dataset.cycle)` localiza el panel cuyo ID coincide con el atributo.

`dataset` convierte atributos `data-*` en propiedades JavaScript.

## 4.6 Objeto `data`

`data` contiene las materias sin repetir HTML. Tiene dos propiedades principales:

- `prog`: Programación.
- `info`: Informática.

Cada orientación contiene años como claves y arrays de materias como valores. Un array se escribe entre `[]` y conserva una colección ordenada.

## 4.7 Función `render(k)`

La función recibe la clave de orientación y construye el acordeón.

### `Object.entries(data[k])`

Convierte el objeto de años en pares `[clave, valor]`.

### `.map(([y,x],i)=>...)`

- `y` es el año.
- `x` es el array de materias.
- `i` es la posición numérica.
- La desestructuración `[y,x]` extrae el par.
- `map()` transforma cada elemento en texto HTML.

### Template literals

Las comillas invertidas permiten texto de varias líneas e interpolación con `${expresión}`.

### `.join('')`

Une los fragmentos del array sin comas.

### `innerHTML`

Inserta el HTML resultante dentro de `#accordion`. El contenido proviene de datos internos controlados, no de entrada del usuario.

Después de crear los botones, se registran eventos para alternar `.open`, actualizar `aria-expanded` y cambiar el símbolo `＋`/`−`.

## 4.8 Cambio de orientación

Los botones `[data-orient]`:

1. Quitan `.active` de todas las orientaciones.
2. Activan la elegida.
3. Ejecutan `render(b.dataset.orient)`.

## 4.9 Modal de especialidades

- `dialog` referencia la ventana nativa.
- `modal` referencia su área de contenido.
- `data-program` permite detectar qué carrera fue elegida.
- La comparación `===` comprueba igualdad estricta.
- El operador ternario `condición ? valorA : valorB` elige texto o listas según la carrera.
- `showModal()` abre el diálogo.
- `.close()` lo cierra.

También se escucha un clic en el propio fondo del `<dialog>`. La condición `e.target===dialog` evita cerrarlo al hacer clic dentro del contenido y solo lo cierra al pulsar el área exterior.

## 4.10 Formulario

El evento `submit` se captura con:

```js
e.preventDefault();
```

Esto evita la recarga y el envío a un servidor inexistente. Después:

- Se escribe un mensaje dentro de `.status` con `textContent`.
- `reset()` vacía los campos.

El mensaje aclara que el formulario necesitará un servicio de correo o backend para realizar un envío real.

---

# 5. Convenciones de nombres

Las clases están en inglés porque es una convención frecuente en desarrollo web:

- `hero`: portada.
- `heading`: encabezado de sección.
- `wrap`: contenedor de ancho limitado.
- `grid`: distribución en cuadrícula.
- `copy`: bloque de texto o texto legal según el contexto.
- `dark`, `white`, `cyan`, `gold`, `yellow`, `blue`: variantes visuales.
- `active`, `open`, `visible`, `scrolled`: clases de estado manipuladas por JavaScript.

Las clases de estado describen qué ocurre, no un componente nuevo. Esto permite que CSS decida la presentación y JavaScript solo cambie el estado.

# 6. Flujo completo de funcionamiento

1. El navegador abre `EESTN2.html`.
2. El `<head>` carga tipografías y `styles.css`.
3. HTML muestra inmediatamente la estructura y el contenido.
4. Al final se carga `script.js`.
5. JavaScript localiza los elementos y registra eventos.
6. `render('prog')` crea inicialmente las materias de Programación.
7. `IntersectionObserver` activa las animaciones a medida que se recorre la página.
8. Los botones y pestañas modifican clases CSS para cambiar estados.
9. Al elegir **Organigrama**, el navegador carga `organigrama.html` como un documento nuevo.
10. En esa página, el botón de regreso vuelve a cargar `EESTN2.html`.

# 7. Accesibilidad aplicada

- Idioma declarado con `lang="es"`.
- Texto alternativo en el escudo.
- Enlace para saltar al contenido.
- Estructura semántica con `header`, `nav`, `main`, `section`, `article`, `aside`, `footer` y jerarquía de títulos.
- Botones reales para acciones interactivas.
- `aria-label`, `aria-expanded`, `role="tablist"` y `role="status"`.
- Contraste alto y fondo oscuro reforzado en el menú.
- Campos asociados a etiquetas.
- Validación nativa mediante `required` y `type="email"`.
- Adaptación a preferencia de movimiento reducido.
- Diseño usable desde teclado gracias a controles HTML nativos.
- Navegación al organigrama mediante un enlace real, por lo que funciona sin JavaScript.
- Contenedor del futuro PNG preparado para escalar sin deformar la imagen.

# 8. Aspectos que requieren servicios externos

La página es estática. Para producción todavía se necesitaría:

- Un backend o servicio de formularios para enviar consultas.
- URLs oficiales para boletín, calendarios y PDFs descargables.
- Datos oficiales completos de teléfono, dirección y horarios.
- Hosting y dominio.
- Un procedimiento de actualización de noticias.

No se almacenan calificaciones ni datos personales. Esto mantiene el alcance seguro e informativo recomendado en la consigna.

# 9. Cómo modificar contenido sin romper el sitio

- Para cambiar textos fijos, editar `EESTN2.html` sin quitar clases ni IDs usados por JavaScript.
- Para cambiar colores globales, editar las variables de `:root`.
- Para cambiar materias, modificar únicamente el objeto `data` de `script.js`.
- Para agregar una especialidad al modal, ampliar los datos y adaptar la condición actual, preferentemente reemplazándola por un objeto de perfiles.
- Para cambiar el escudo, conservar el nombre `Escudo.png` o actualizar ambos atributos `src`.
- Para incorporar el organigrama, insertar un elemento `<img>` dentro de `#organigrama-contenedor` en `organigrama.html` y usar un texto `alt` descriptivo.
- Para cambiar el destino del menú Organigrama, editar `href="organigrama.html"` en la navegación principal.
- Para modificar el botón de regreso, conservar un enlace hacia `EESTN2.html` o hacia el nombre definitivo de la página principal.
- Para conectar el formulario, reemplazar el controlador de `submit` por una solicitud `fetch()` hacia un servicio seguro.

Esta arquitectura mantiene una separación clara: HTML describe, CSS presenta y JavaScript controla los estados interactivos.
