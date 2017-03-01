# vue-methods-promise
```
Let Vue methods support promise
```

### Usage
-  Page introduction
```html
  <div id="app"></div>
  <script src="https://cdn.jsdelivr.net/vue/latest/vue.js"></script>
  <script src="./dist/vue-methods-promise.js"></script>
  <script>
    vueMethodsPromise(Vue, {
      hookName: '$promise', // Component default hook name
      promise: function (mp) { // Promise callback default Unified processing error
        mp
          .catch(function (err) {
            console.log(mp)
          })
      }
    })

    new Vue({
      el: '#app',
      mounted: function () {
        this.init()
      },
      methods: { // 
        init: function () {
          return new Promise(function (resolve, reject) {
            setTimeout(reject, 500)
          })
        },
        $promise (mp) { // Optional parameters
          return mp.then(function () {
            // 
          })
        }
      }
    })

  </script>
```
- npm
```
npm install --save vue-methods-promise
```
```javascript
import Vue from 'vue'
import vueMethodsPromise from 'vue-methods-promise'

Vue.use(vueMethodsPromise, {
  hookName: '$promise', // Component default hook name
  promise: (mp) => { // Promise callback default Unified processing error
    mp
      .catch(function (err) {
        console.log(mp)
      })
  }
})
```