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
    
