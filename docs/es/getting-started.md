# Empezando

En el centro de cada aplicación Vuex esta el **almacen** (store). el "Almacén es básicamente un contenedor que contiene el **estado** de la aplicación. Hay dos cosas que hacen al almacén de Vuex diferente a un objecto plano global:

1. Los almacenes de Vuex son reactivos. Cuando un componente de Vue obtiene el estado de el, el componente reaccionara y se actualizara efectivamente cuando el estado del almacén se actualize.

2. No podrás mutar el estado del almacén directamente. La única forma de cambiar el estado del almacén es explícitamente **ejecutando una mutaciones (commiting mutations)**. Esto asegura que cada cambio de estado, deje un rastro y habilita otras herramientas que nos ayudaran a entender mejor nuestras aplicaciones.

### El almacén mas simple:

> **NOTA:** Para el resto de la documentacion estaremos usando la sintaxis ES2015 para los ejemplos de código. Si no la ha utilizado, [aquí podra comenzar](https://babeljs.io/docs/learn-es2015/)!

Después de la [instalación](installation.md) de Vuex, creemos un almacén. Es bastante simple - solo provea un estado inicial, y algunas mutaciones:

``` js
// Asegúrese de llamar Vue.use(Vuex) primero, en caso de estar utilizando un sistema modular

const store = new Vuex.Store({
  state: {
    count: 0
  },
  mutations: {
    increment (state) {
      state.count++
    }
  }
})
```
Ahora, usted puede acceder el estado del objeto `store.state`, y ejecutar un cambio de estado usando el método `store.commit`:

``` js
store.commit('increment')

console.log(store.state.count) // -> 1
```

De nuevo, la razón por la que estamos ejecutando una mutación en lugar de cambiar el `store.state.count` directamente, es por que queremos explícitamente rastrear sus cambios. Esta simple costumbre hace tu intención mas explicita, entonces podrá entender los cambios de estado en su aplicación de una mejor manera cuando lea el código. Adicionalmente, esto nos da la oportunidad de implementar herramientas que pueden registrar cada mutación, tomar capturas de estado, e inclusive utilizar depuración de viaje en el tiempo (time travel debugging).

Usando el estado del almacén en un componente simplemente require regresar el estado como una propiedad calculada (computed property) por que el estado es reactivo. Ejecutar cambios simplemente significa ejecutar mutaciones en métodos dentro de los componentes.

Aquí encontrara un ejemplo [una aplicación básica de contador en Vuex](https://jsfiddle.net/yyx990803/n9jmu5v7/).

Después, discutiremos cada uno de los conceptos de una manera mas detallada comenzando con el [Estado (State)](state.md).
