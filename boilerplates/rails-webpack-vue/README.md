# Ruby on Rails with Webpack and Vue

## config/webbpack/loaders/vue.js

```js

const { dev_server: devServer } = require('@rails/webpacker').config

const isProduction = process.env.NODE_ENV === 'production'
const inDevServer = process.argv.find(v => v.includes('webpack-dev-server'))
const extractCSS = !(inDevServer && (devServer && devServer.hmr)) || isProduction

module.exports = {
  test: /\.vue(\.erb)?$/,
  use: [{
    loader: 'vue-loader',
    options: { extractCSS }
  }]
}

```

## config/webpack/environment.js

```js
const { environment } = require('@rails/webpacker')
const vue =  require('./loaders/vue')

environment.loaders.append('vue', vue)
module.exports = environment

```

## package.json

```
{
  "name": "project",
  "private": true,
  "dependencies": {
    "@rails/webpacker": "3.5",
    "vue": "^2.5.17",
    "vue-loader": "14.2.2",
    "vue-resource": "^1.5.1",
    "vue-template-compiler": "^2.5.17",
    "vue-turbolinks": "^2.0.3"
  },
  "devDependencies": {
    "webpack-dev-server": "2.11.2"
  }
}

```

## app/javascript/packs/application.js

```js
import Vue from 'vue/dist/vue.esm'

import TurbolinksAdapter from 'vue-turbolinks';
import VueResource from 'vue-resource'

Vue.use(VueResource);
Vue.use(TurbolinksAdapter);

document.addEventListener('turbolinks:load', () => {
  Vue.http.headers.common['X-CSRF-Token'] = document.querySelector('meta[name="csrf-token"]')
    .getAttribute('content');

  // let token = document.getElementsByName('csrf-token')[0].getAttribute('content');
  // axios.defaults.headers.common['X-CSRF-Token'] = token;
  // axios.defaults.headers.common['Accept'] = 'application/json';

  const app = new Vue({
    el: '[data-behavior="vue"]',
  });
});

```
