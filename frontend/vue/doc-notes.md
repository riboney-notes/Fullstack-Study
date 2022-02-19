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

- To toggle more than one element with `v-if`, put `v-if` on the `template` tag and house all the elements to toggle inside there
- Difference between `v-if` and `v-show`
   - element with `v-show` will always be rendered and remain in the DOM
      - it only toggles the display CSS property
      - v-if removes element in and out of dom while v-show just changes the display
   - `v-show` does not support template element nor does it work with v-else  

- `v-if` has higher priority than `v-for`
   - in order to nest `v-if` inside `v-for` (and allow `v-if` to access the variables in `v-for`), move `v-for` in template and use `v-if` inside the template

- maintan the order of state and rendering for `v-for` with `key`
   - needed when list rendering depends on child component state or some other state 
   - do not use `objects` for `key`..keep it primitive
```js
<template v-for="todo in todos" :key="todo.name">
  <li>{{ todo.name }}</li>
</template>
```
- to pass data from `v-for` into componets, use props:
```js
<my-component
  v-for="(item, index) in items"
  :item="item"
  :index="index"
  :key="item.id"
></my-component>
```

- you can invoke methods rather than pass them in as callbacks in template (ex: `@click="onClick('some arg')`) instead of just `@click="onClick"`
- Access `event` with `$event` if using a function or just pass in `event` if using inline arrow function (see [link](https://vuejs.org/guide/essentials/event-handling.html#accessing-event-argument-in-inline-handlers))
- Instead of dealing with DOM stuff inside handlers, like for calling `event.prevent` or `event.stop`, etc...you can use event modifiers for `v-on` to modify some handler without having to explicitly modify it inside the handler function

![image](https://user-images.githubusercontent.com/14286113/154814405-97339156-7ca8-473e-93dd-593d26b4dc67.png)

- `v-model` simplifies binding to the value attribute in input tags
- can add modifiers to `v-model` to change how it behaves
   - `.lazy` modifier will have the v-model sync input with the data after `change` events
   - `.trim` will automatically trim whitespace 

- Tempalte refs can be used to directly access DOM elements from `script setup`
   - for refs used inside `v-for`, ref should contain an array value which would be populated with elements after mount 

## Reactivity

```js
import { reactive } from 'vue'

export default {
  // `setup` is a special hook dedicated for composition API.
  setup() {
    const state = reactive({ count: 0 })

    function increment() {
      state.count++
    }
    
    // expose the state to the template
    return {
      state,
      increment
    }
  }
}

<div>{{ state.count }}</div>
<button @click="increment">
  {{ state.count }}
</button>
```

- Can use `<script setup>` instead of `setup()` to expose state and methods
   - can be done in SFCs 
   - top-level imports and variables declared in `<script setup>` are usable in the template of the same component
```js
<script setup>
import { reactive } from 'vue'

const state = reactive({ count: 0 })

function increment() {
  state.count++
}
</script>

<template>
  <button @click="increment">
    {{ state.count }}
  </button>
</template>
```

- DOM updates happen with every "tick" in the update cylce
   - use `nextTick(cb)` to wait for DOM update to complete after a state change and execute some method and/or access the updated DOM

- Reactive() has some limitations
   - only works for object types; can't hold primitive types
   - Must keep same reference to reactive object and can't easily replace it

- can use `ref()` to create reactive refs that hold any value type
   - it takes an argument and returns it wrapped within a ref object, and can be accessed with that ref's object's `value` property
   - refs are automatically unwrapped in the HTML so no need to use the `.value` to `{{}` to get access to the ref value
      - Only applies to top-level properties, not refs that are nested inside some object  

## Computed properties

- in-template expressions are meant for simple operations
- to reduce clutter in the HTML and for complex logic, use computed properties

```js
// not using computed property
const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})
<p>Has published books:</p>
<span>{{ author.books.length > 0 ? 'Yes' : 'No' }}</span>

// using computed properties
<script setup>
import { reactive, computed } from 'vue'

const author = reactive({
  name: 'John Doe',
  books: [
    'Vue 2 - Advanced Guide',
    'Vue 3 - Basic Guide',
    'Vue 4 - The Mystery'
  ]
})

// a computed ref
const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
})
</script>

<template>
  <p>Has published books:</p>
  <span>{{ publishedBooksMessage }}</span>
</template>
```

- `computed()` takes a function and returns a computed ref, which is like a normal ref in that you access the value by `.value`
   - computed refs are auto-unwrapped in HTML like refs
- computed property automatically racks its reactive dependencies and updates bindings when state changes

- Computed properties vs using methods
   - Main difference is that computed properties are cached based on their reactive dependencies
      - meaning that it will only re-evaluate when some of its reactive dependencies have changed
      - if not changed, then cached results are returned without running function again
   - Methods on the other hand, always *execute* when a re-render happens
- So, use computed properties to handle heavy computations that you wouldn't want to constantly execute unless its dependencies state changes
- Computed properties only *get* values, not change them (By default)
   - assinging new value to a computed property will cause warning
   - provide a setter to computed properties to be able to change values of the reactive dependencies
    ![image](https://user-images.githubusercontent.com/14286113/154812008-43000529-a9c0-4a4b-8839-9ebd8493c2e1.png)

- Try to keep getters in computed property, side-effect free
   - don't make async requests or mutate the DOM inside of the computed getter
   - computed property getter should mainly be retrieving a value based on other reactive values   
   - leave the side effects for vue watchers
- Avoid mutating the computed value
   - the returned value from a computed property is like a snapshot of all the reactive dependencies involved
   - everytime dependencies change, the snapshot changes
   - therefore, it should be treated as read-only and never mutated since that goes against the intent of computed properties
- To trigger new computations, update its reactive dependencies  

## Class and style bindings

- v-bind for class and styles is different than for binding with other attributes
- Objects can be passed to `:class` to toggle class
   - Ex: `<div :class="{ active: isActive }"></div>`; class will be set to `active` if `isActive` is true
   - multiple objects can be passed to `:class` (just add more fields to the object you pass in)
      - declare this object elsewhere and refer to it in the template (it doesn't have to be declared in-line)  
      - can also use a computed-property:
      ![image](https://user-images.githubusercontent.com/14286113/154812858-cb15ded2-b040-4b62-84be-50ba819ca64d.png)

- Can pass array to apply a list of classes to `:class`
   - Using ternary expression: `<div :class="[isActive ? activeClass : '', errorClass]"></div>`
- you can use the normal HTML class attribute in conjunction with `:class`
- Attributes like `class` can be inherited from multiple root elements

## Watchers

- `watch()` can be used to trigger some callback whenever a piece of reactive state changes

```js
<script setup>
import { ref, watch } from 'vue'

const question = ref('')
const answer = ref('Questions usually contain a question mark. ;-)')

// watch works directly on a ref
watch(question, async (newQuestion, oldQuestion) => {
  if (newQuestion.indexOf('?') > -1) {
    answer.value = 'Thinking...'
    try {
      const res = await fetch('https://yesno.wtf/api')
      answer.value = (await res.json()).answer
    } catch (e) {
      answer.value = 'Error! Could not reach the API. ' + error
    }
  }
})
</script>

<template>
  <p>
    Ask a yes/no question:
    <input v-model="question" />
  </p>
  <p>{{ answer }}</p>
</template>
```

- `watch()` is lazy, `watchEffect()` is not and performs side effect immediately
- user-created watchers are called before DOM updates (so you can't access DOM and get updated values)
   - in order to access DOM after Vue updates it, specify the `flush: post` option or use `watchPostEffect`
- if watcher is created in callback/ async method, then you must stop it manually 
