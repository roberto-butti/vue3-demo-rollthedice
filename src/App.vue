<template>
<!-- ##001: use the componennt in template -->
  <RollTheDice />
</template>

<script>
// ##002: import the component
import RollTheDice from './components/RollTheDice.vue'

export default {
  name: 'App',
  components: {
    // ##003: declare the component
    RollTheDice
  }
}
</script>
