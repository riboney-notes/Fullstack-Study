# Vue Notes from Documentation

## Intro

Two core features of Vue:
   - Declarative Rendering: Dynamic HTML display based on JS state
   - Reactivity: Automatic updates to DOM when changes to state happen

Single-File Components (SFC)
   - AKA `.vue` files
   - Encapsulates the component's logic (JS), template (HTML), and styles (CSS) in a single file
   - Ex:
   ```js
   <script>
    // example of Options API
    export default {
      data() {
        return {
          count: 0
        }
      }
    }
    </script>

    <template>
      <button @click="count++">Count is: {{ count }}</button>
    </template>

    <style scoped>
      button {
        font-weight: bold;
      }
    </style>
   ```

API Styles:
  - Options API: component's logic defined by an object of options such as `data`, `methods,` etc
    - Properties defined by options can be referred to by `this` inside of functions in the SFC
  - Composition API: dfine component's logic using imported API functions
    - Imports, top-level variables, and functions can be declared inside `<script setup>` tags to be directly usable in the template
    - Ex:
    ```js
    <script setup>  
    import { ref, onMounted } from 'vue'

    // reactive state
    const count = ref(0)

    // functions that mutate state and trigger updates
    function increment() {
      count.value++
    }

    // lifecycle hooks
    onMounted(() => {
      console.log(`The initial count is ${count.value}.`)
    })
    </script>

    <template>
      <button @click="increment">Count is: {{ count }}</button>
    </template>
    ```      
    
## Tips

- Can capture app-level errors by setting `errorhandler` to the `config` object in the application instance, and have it receieve error objects

   ```js
      app.config.errorHandler = (err) => //handle error
   ```

- Text interpolation from `{{ }}` outputs plain text, not HTML
   - Can't directly change HTML with `{{}}`
   - Use `v-html` directive to output real HTML and have it take effect on the rest of the pages HTML content
      - Security: only use on trusted content and not user-provided content to prevetn XSS vuln.

- Mustaches `{{}}` can not be used inside HTML attributes
   - Must use directives such as `v-bind` to use JS code in HTML tags
- Empty strings are considered to be `true` in v-bindings (not false like how it usually is in JS)

- Bind multiple attributes in an object and then bind them in a HTML tag by binding with the object itself

```js
const objectOfAttrs = {
  id: 'container',
  class: 'wrapper'
}
<div v-bind="objectOfAttrs"></div>
```

- Only use javascript expression in the HTML
   - Statemetns such as `let a = 1` is not valid
   - Flow control such as if-else statements are not valid
      - Use ternary expressions instead
- Functions declared to be called in the HTML in a binding way, will be called every time the cocmpnent updates
   - So they should not have any side effects such as changing data or triggering async operations

- Can add global values (ex: window) to the expressions in HTML by adding them to `app.config.globalProperties`   

- Can create dynamic arguments for directives by wrapping the argument in `[]`
   - Can be used for `v-bind` and `v-on`
   - Ex: `v-on:[eventName] = "do somehting..."
   - dynamic arguments returns a string or null; otherwise, you get warning
   - dynamic arguments have restrictions on what characters you can use since its supposed to be valid HTML attribute names
   - Alternative to dynamic argument is computed property
   - avoid use of capital letters in attributes
   - <img src="https://vuejs.org/assets/directive.69c37117.png" alt="directive syntax graph"/>![image](https://user-images.githubusercontent.com/14286113/154809388-c6f361b8-d7a9-4bb3-aa13-541c3ab0c088.png)

## Reactivity
