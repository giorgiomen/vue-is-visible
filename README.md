# Description
This is a Vue component that emits an event when the component is visible within the browsers viewport.


## Usage

### NPM

```
$ npm install vue-is-visible
```

### Global usage

```
import Vue from 'vue'
import { VueIsVisible } from 'vue-is-visible'
Vue.use(VueIsVisible)
```

### Local usage

```
import { VueIsVisible } from 'vue-is-visible'
export default {
  components: {
    VueIsVisible
  }
}
```


### API


#### `event` - number

The name of the event to be emitted when the component is visible within the browsers viewport.


### Example

```
<template>
  <vue-is-visible event="isVisible" v-on:isVisible="setBackgroundColor">
    <div v-bind:style="{backgroundColor}">
      Hello
    </div>
  </vue-is-visible>
</template>
```

```
<script>
  import { VueIsVisible } from 'vue-is-visible'
  export default {
    components: {
      VueIsVisible
    },
    data() {
      return {
        backgroundColor: 'white'
      }
    },
    methods: {
      setBackgroundColor() {
        this.backgroundColor = 'blue'
      }
    }
  }
</script>
```
