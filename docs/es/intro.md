# Que es Vuex?

Vuex es una **librería de patrón de manejo de estado** para aplicaciones Vue.js. Sirve como un almacén centralizado para todos los componentes en una aplicación, con reglas que garantizan que el almacén solo puede ser alterado de formas predecibles. También se integra con la herramientas de desarrollador oficial de Vue [extension de desarrollador](https://github.com/vuejs/vue-devtools) la cual provee características avanzadas como, cero configuración, depuración con viaje en el tiempo, capturas de estado con importación y exportación.

### Que es un "Patron de Manejo de Estado"?

Empecemos con una aplicación de conteo simple en Vue:

``` js
new Vue({
  // estado (state)
  data () {
    return {
      count: 0
    }
  },
  // vista (view)
  template: `
    <div>{{ count }}</div>
  `,
  // acciones (actions)
  methods: {
    increment () {
      this.count++
    }
  }
})
```
Es una aplicación auto-contenida con las siguientes partes:

- El **estado**, que es la fuente de la verdad que dirige nuestra aplicación;
- La **vista**, que es solo la declaración que representa el **estado**;
- Las **acciones**, que son las opciones posibles en las cuales el estado puede cambiar en reacción a las acciones del usuario desde la **vista**;

Esta es una representación extremadamente simple del concepto de "flujo de datos de un sentido":

<p style="text-align: center; margin: 2em">
  <img style="max-width:450px;" src="./images/flow.png">
</p>

Sin embargo, la simplicidad se rompe rápidamente cuando tenemos **multiples componentes que comparten el mismo almacén**:

- Multiples vistas que pueden depender de una misma parte del almacén.
- Acciones de diferentes vistas tienen la necesidad de mutar la misma parte de un almacén.

Para el problema uno, pasar propiedades (props) puede ser tedioso para componentes que se encuentren profundamente anidados, y simplemente no funciona para componentes hermanos. Para el problema dos, a menudo nos encontramos recurriendo a soluciones como obtener referencias directas de la instancias padre/hijo, o tratando de mutar y sincronizar copias multiples del almacén via eventos. Estos dos patrones son frágiles y rápidamente nos llevan a código no mantenible.

Entonces por que no extraemos el almacén compartido de los componentes, y lo manejamos en un singleton global? con esto, nuestro árbol de componentes se convierte en una gran "vista", y cualquier componente puede acceder el estado o ejecutar acciones, no importando su ubicación en el árbol!

Adicionalmente, si definimos y separamos los conceptos involucrados en el manejo de estados y forzando ciertas reglas, también le damos a nuestro código mas estructura y mantenibilidad.

La idea basica detras de Vuex, esta inspirada por [Flux](https://facebook.github.io/flux/docs/overview.html), [Redux](http://redux.js.org/) y [La Arquitectura Elm](https://guide.elm-lang.org/architecture/). Diferente a otros patrones, Vuex también es una librería hecha a la medida específicamente para Vue.js tomando ventaja de su sistema de reacción granular para actualizaciones eficientes. 

![vuex](./images/vuex.png)

### Cuando debería ulitizarlo?

A pesar de que Vuex nos ayuda a manejar el almacén compartido, también viene con el costo de mas conceptos por aprender y código biolerplate. es un intercambio entre productividad a corto plazo con productividad a largo plazo.

Si nunca has construido una SPA (Aplicación de una Sola Pagina) de gran escala y utilizas Vuex, podrás sentirlo demasiado verboso y desalentador. Eso es perfectamente normal - si tu aplicación es simple, probablemente estarás bien sin Vuex. Un simple [evento global y comunicación padre/hijo](http://vuejs.org/guide/components.html#Non-Parent-Child-Communication) sera todo lo que necesites. Pero si, estas creando una SPA tamaño medio-grande, tal vez encuentres situaciones que te harán pensar en como manejar el almacén fuera de tus componentes en Vue, y Vuex sera el paso natural a seguir para ti.
Hay un buen dicho de Dan Abramov, el author de Redux:

> Las librerías Flux son como los anteojos: tu sabras, cuando los necesites.

