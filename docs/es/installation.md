# Instalacion

### Descarga Directa / CDN

[https://unpkg.com/vuex](https://unpkg.com/vuex)

<!--email_off-->
[Unpkg.com](https://unpkg.com) provee enlaces CDN basados en NPM. El enlace anterior siempre apuntara a el ultimo lanzamiento en NPM. También puedes usar una version o tag especifico usando enlaces como el que se muestra a continuación: `https://unpkg.com/vuex@2.0.0`.
<!--/email_off-->

Incluye `vuex` después de Vue y `vuex` instalara automáticamente:

``` html
<script src="/path/to/vue.js"></script>
<script src="/path/to/vuex.js"></script>
```

### NPM

``` bash
npm install vuex
```

### Yarn

``` bash
yarn add vuex
```

Cuando se utilize en sistemas modulares, tendrá que explícitamente instalar Vuex usando `Vue.use()`:

``` js
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)
```

No necesitara hacer esto cuando se utilicen etiquetas de script (`script tags`) globales.

### Version de Desarrollo (Dev Build)

Tendrá que clonar directamente de Github y construir `vuex` si quiere utilizar la ultima versión de desarrollo (dev build):

``` bash
git clone https://github.com/vuejs/vuex.git node_modules/vuex
cd node_modules/vuex
npm install
npm run build
```
