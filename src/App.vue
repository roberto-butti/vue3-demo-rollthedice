<script>
// ##002: import the component
import RollTheDice from './components/RollTheDice.vue'
import RollTheDiceReactive from './components/RollTheDiceReactive.vue';
export default {
  name: 'App',
  components: {
    // ##003: declare the component
    RollTheDice,
    RollTheDiceReactive
}
}
</script>

<template>
<!-- ##001: use the component in template -->
  <RollTheDice />
  <RollTheDiceReactive />
</template>


