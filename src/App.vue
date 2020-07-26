<template>
<!-- ##001: use the componennt in template -->
  <RollTheDiceReactive />
</template>

<script>
// ##002: import the component
import RollTheDiceReactive from './components/RollTheDiceReactive.vue'

export default {
  name: 'App',
  components: {
    // ##003: declare the component
    RollTheDiceReactive
  }
}
</script>
