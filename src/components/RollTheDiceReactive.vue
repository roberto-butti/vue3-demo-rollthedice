<template>
  <h1>Number is: {{ game.dice }}</h1>
  <div>Number of rolls: {{ game.rolls.length }}</div>
  <div>Total: {{ total }}</div>
  <button @click="roll()">Let's roll the dice</button>
  <button @click="restart()">Restart</button>
  <ul>
    <li  v-for="(t, index) in rolls" :key="index">
       {{ t }}
    </li>
  </ul>
</template>

<script>
// ##001 : import reactive and computed from vue3
import { reactive, computed } from "vue";
export default {
  name: 'RollTheDiceReactive',

  // ##002 : implement setup function
  setup() {

    // ##003 : declare and initialize reactive object with 2 properties: dice and rolls
    const game = reactive(
        {
            dice: 0,
            rolls: []
        }
    )

    // ##004: implement roll function (inside setup() )
    function roll() {
      game.dice = Math.floor(Math.random() * Math.floor(5)) + 1;
      game.rolls.unshift(game.dice);
    }

    // ##005: implement restart function (inside setup() )
    function restart() {
      game.dice=0
      game.rolls = [];
    }

    // ##006: define a computed function (total)
    const total = computed(() => {
      let temptotal = 0;
      for (let i=0 ; i< game.rolls.length; i++) {
        temptotal = temptotal + game.rolls[i]
      }
      return temptotal;
    });

    // ##007: expose to the template all stuff (variables, functions, computed etc)
    return { game, total, roll, restart };
  }
}
</script>
