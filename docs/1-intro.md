
---


## Introducción a los componentes en Svelte

En Svelte, una aplicación está compuesta por uno o más componentes. Un componente es un bloque de código autónomo y reutilizable que encapsula HTML, CSS y JavaScript relacionados, y se escribe en un archivo con extensión `.svelte`. El archivo `App.svelte`, que se encuentra abierto en el editor de código a la derecha, es un ejemplo de un componente simple.

**Agregar datos:**

Un componente que solo contiene marcado estático no es muy interesante. Vamos a agregar algunos datos.

Primero, agregamos una etiqueta `<script>` a nuestro componente y declaramos una variable `name`:

```html
<script>
	let name = 'Svelte';
</script>

<h1>Hello world!</h1>
```

Luego, podemos referirnos a `name` en el marcado:

```html
<h1>Hello {name}!</h1>
```

Dentro de los corchetes `{}`, podemos colocar cualquier JavaScript que deseemos. Intenta cambiar `name` a `name.toUpperCase()` para un saludo en mayúsculas.

```html
<h1>Hello {name.toUpperCase()}!</h1>
```

Al igual que podemos usar corchetes para controlar el texto, también podemos usarlos para controlar los atributos de los elementos.

Nuestra imagen carece de un `src`. Añadamos uno:

```html
<img src={src} />
```

Es mejor, pero si pasas el ratón sobre la `<img>` en el editor, Svelte nos advierte:

"A11y: El elemento 'img' debe tener un atributo alt"

Es importante asegurarse de que las aplicaciones web sean accesibles para la mayor cantidad de usuarios posible, incluidas personas con discapacidades visuales o motoras, o personas con conexiones a Internet lentas. La accesibilidad (abreviada como a11y) no siempre es fácil de lograr, pero Svelte te ayudará advirtiéndote si escribes un marcado inaccesible.

En este caso, nos falta el atributo `alt` que describe la imagen para personas que utilizan lectores de pantalla o que tienen conexiones a Internet lentas o limitadas. Añadamos uno:

```html
<img src={src} alt="Un hombre baila." />
```

Podemos utilizar corchetes para enlazar variables dentro de atributos. Intenta cambiarlo a `alt="{name} dances."`. Recuerda declarar una variable `name` en el bloque `<script>`.

**Atributos de manera abreviada:**

No es raro tener un atributo donde el nombre y el valor son los mismos, como `src={src}`. Svelte nos proporciona una abreviatura conveniente para estos casos:

```html
<img {src} alt="{name} dances." />
```

---

**Agregando estilos a un componente en Svelte:**

Al igual que en HTML, puedes agregar una etiqueta `<style>` a tu componente para aplicar estilos CSS. Veamos cómo agregar algunos estilos al elemento `<p>`:

```html
<p>This is a paragraph.</p>

<style>
	p {
		color: goldenrod;
		font-family: 'Comic Sans MS', cursive;
		font-size: 2em;
	}
</style>
```

Es importante que estas reglas de estilo estén en el ámbito de aplicación del componente. Esto significa que no cambiarás accidentalmente el estilo de los elementos `<p>` en otras partes de tu aplicación. Svelte se encarga de asegurar que los estilos definidos en un componente se apliquen solo a ese componente específico.

---

Con estos estilos, el elemento `<p>` dentro de tu componente ahora tendrá un color dorado (`goldenrod`), una fuente de texto de tipo 'Comic Sans MS' o una fuente similar, y un tamaño de fuente dos veces más grande que el tamaño predeterminado.
