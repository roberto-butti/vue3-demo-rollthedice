<template>
  <h1>Using ref()</h1>
  <h2>Number is: {{ dice }}</h2>
  <div>Number of rolls: {{ rolls.length }}</div>
  <div>Total: {{ total }}</div>
  <button @click="roll()">Let's roll the dice</button>
  <button @click="restart()">Restart</button>
  <ul>
    <li  v-for="(t, index) in rolls" :key="index">
       {{ t }}
    </li>
  </ul>
</template>

<script setup>
// ##001 : we are using script setup 
// ##002 : import ref and computed from vue3
import { ref, computed } from "vue";

// ##003 : declare and initialize 2 reactive variables dice and rolls
const dice = ref(0);
const rolls = ref([]);
// ##004: implement roll function (inside setup() )
function roll() {
    dice.value = Math.floor(Math.random() * Math.floor(5)) + 1;
    rolls.value.unshift(dice.value);
}
// ##005: implement restart function (inside setup() )
function restart() {
    dice.value = 0
    rolls.value = [];
}
// ##006: define a computed function (total)
const total = computed(() => {
    let temptotal = 0;
    for (let i = 0; i < rolls.value.length; i++) {
        temptotal = temptotal + rolls.value[i]
    }
    return temptotal;
});
</script>