# vue-instant-bootstrap-modal

> Bootstrap modal component for use with awesome Vue

## Installation

``` bash
# yarn
yarn add vue-instant-bootstrap-modal

# npm
npm install --save vue-instant-bootstrap-modal
```

## Example

### Markup

``` html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>vue-instant-bootstrap-modal</title>
    <link rel="stylesheet" href="https://maxcdn.bootstrapcdn.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
  </head>
  <body>
    <div id="app">
      <vue-instant-bootstrap-modal ref="Modal">
        <div class="modal-header">
          <h4>This is modal header</h4>
        </div>
        <div class="modal-body">
          This is modal body
        </div>
        <div class="modal-footer">
          <button class="btn btn-info" @click="$refs.Modal.hide()">
            Close modal
          </button>
        </div>
      </vue-instant-bootstrap-modal>
      <button class="btn btn-primary" @click="$refs.Modal.show()">
        Open modal
      </button>
    </div>
    <!-- your script goes here -->
  </body>
</html>
```

### Script

``` javascript
import Vue from 'vue'
import VueInstantBootstrapModal from 'vue-instant-bootstrap-modal'

new Vue({
  el: '#app',
  components: { VueInstantBootstrapModal },
});
```

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test
```

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
