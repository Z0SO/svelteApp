
---



## **Creando un componente en Svelte:**

Cuando creas un componente en Svelte, puedes usar la etiqueta `<script>` para incluir bloques de código JavaScript. Este código se ejecuta cuando se crea una instancia del componente y las variables declaradas en este bloque son visibles para el marcado del componente. Aquí hay algunas reglas importantes:

1. **Exportación crea un elemento:**
   En Svelte, usamos la palabra clave `export` para marcar una variable como un atributo del componente, lo que significa que será accesible desde fuera del componente. Esto es útil para pasar datos al componente desde su contexto padre. Por ejemplo:

   ```html
   <script>
     export let foo;

     // Los valores pasados como atributos son accesibles de inmediato
     console.log({ foo });
   </script>
   ```

2. **Valor inicial predeterminado para los atributos:**
   Puedes especificar un valor inicial predeterminado para un atributo. Este valor se utilizará si el consumidor del componente no proporciona un valor específico al instanciar el componente. Por ejemplo:

   ```html
   <script>
     export let bar = 'valor inicial opcional';
     export let baz = undefined;
   </script>
   ```

3. **Exportar constantes, clases y funciones:**
   Si exportas una constante, clase o función, estas serán accesibles desde fuera del componente. Las funciones son valores de apoyo válidos y pueden ser útiles para acciones específicas del componente. Por ejemplo:

   ```html
   <script>
     // estas son de solo lectura
     export const thisIs = 'solo lectura';

     /** @param {string} name */
     export function greet(name) {
       alert(`¡Hola ${name}!`);
     }
   </script>
   ```

4. **Acceso a atributos de lectura mediante la sintaxis `bind:this`:**
   Puedes acceder a atributos de lectura como propiedades en el elemento del componente usando la sintaxis `bind:this`. Esto es útil para interactuar con el DOM del componente desde su contexto padre. Por ejemplo:

   ```html
   <script>
     /** @type {string} */
     let className;

     // crea una propiedad `class`, aunque sea una palabra reservada
     export { className as class };
   </script>
   ```


---

## **Reactividad en Svelte:**

En Svelte, las asignaciones son 'reactivas', lo que significa que cuando asignas un nuevo valor a una variable, esto desencadena automáticamente una actualización en el componente y provoca que se vuelva a renderizar.

1. **Cambiar el estado del componente:**
   Para cambiar el estado de un componente y desencadenar una re-renderización, simplemente asigna un nuevo valor a una variable localmente declarada. Por ejemplo:

   ```html
   <script>
     let count = 0;

     function handleClick() {
       // al llamar a esta función se desencadena una actualización si el marcado referencia `count`
       count = count + 1;
     }
   </script>
   ```

   Tanto la actualización de expresiones (`count += 1`) como la asignación directa (`count = newValue`) tienen el mismo efecto.

2. **Actualización de arreglos:**
   Sin embargo, los métodos de los arreglos, como `.push()` y `.splice()`, no activan automáticamente las actualizaciones. Después de modificar un arreglo con estos métodos, necesitas hacer una asignación posterior para activar la actualización. Por ejemplo:

   ```html
   <script>
     let arr = [0, 1];

     function handleClick() {
       // esta llamada al método no desencadena una actualización
       arr.push(2);
       // esta asignación desencadenará una actualización si el marcado referencia `arr`
       arr = arr;
     }
   </script>
   ```

3. **Asignaciones en bloques `<script>`:**
   Los bloques `<script>` en Svelte se ejecutan solo cuando se crea el componente, por lo que las asignaciones dentro de estos bloques no se ejecutan automáticamente nuevamente cuando una variable cambia. Si deseas rastrear los cambios en una variable, necesitas asignarla explícitamente. Por ejemplo:

   ```html
   <script>
     export let person;
     // esto solo establecerá `name` en la creación del componente
     // no se actualizará cuando `person` lo haga
     let { name } = person;
   </script>
   ```

---


---
