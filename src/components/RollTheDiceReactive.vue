<template>
  <h1>Number is: {{ dice }}</h1>
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

<script>
// ##001 : import from vue3:
// - reactive for making properties reactive;
// - computed for computed function like total
// - toRefs for destructuring object for template
import { reactive, computed, toRefs } from "vue";
export default {
  name: 'RollTheDiceReactive',
  // ##002 : implement setup function
  setup() {
    // ##003 : declare and initialize reactive object
    const game = reactive(
        {
            dice: 0,
            rolls: [],
            // ##004 : we include also computed properties in game object
            total: computed(
              () => {
                let temptotal = 0;
                for (let i=0 ; i< game.rolls.length; i++) {
                  temptotal = temptotal + game.rolls[i]
                }
                return temptotal;
              }
            )
        }
    )
    // ##005: implement roll function (inside setup() )
    function roll() {
      game.dice = Math.floor(Math.random() * Math.floor(5)) + 1;
      game.rolls.unshift(game.dice);
    }

    // ##06: implement restart function (inside setup() )
    function restart() {
      game.dice=0
      game.rolls = [];
    }

    // ##007: expose to the template all stuff (object, functions etc)
    return {
      ...toRefs(game), //data
      roll, restart //functions
    };
  }
}
</script>
