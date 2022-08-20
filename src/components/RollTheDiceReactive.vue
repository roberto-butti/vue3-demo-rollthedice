<template>
  <h1>Using reactive()</h1>
  <h2>Number is: {{ game.dice }}</h2>
  <div>Number of rolls: {{ game.rolls.length }}</div>
  <div>Total: {{ game.total }}</div>
  <button @click="roll()">Let's roll the dice</button>
  <button @click="restart()">Restart</button>
  <ul>
    <li v-for="(t, index) in game.rolls" :key="index">
      {{ t }}
    </li>
  </ul>
</template>

<script setup>
// ##001 : we are using script setup
// ##002 : import from vue3:
// - reactive for making properties reactive;
// - computed for computed function like total
import { reactive, computed, toRef } from "vue";
const game = reactive(
  {
    dice: 0,
    rolls: [],
    // ##003 : we include also computed properties in game object
    total: computed(
      () => {
        let temptotal = 0;
        for (let i = 0; i < game.rolls.length; i++) {
          temptotal = temptotal + game.rolls[i]
        }
        return temptotal;
      }
    )
  }
)

// ##004: implement roll function
function roll() {
  game.dice = Math.floor(Math.random() * Math.floor(5)) + 1;
  game.rolls.unshift(game.dice);
}
// ##005: implement restart function
function restart() {
  game.dice = 0
  game.rolls = [];
}
</script>
