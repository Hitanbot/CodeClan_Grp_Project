<template lang="html">
  <div>
    <button v-on:click="rollDice()" v-onclick="">Roll Dice</button>
    <!-- <input type="image" src="../assets/dice.jpg" name="rollDice" class="btTxt submit" id="rollDice" /> -->
    <div v-if="diceResult">
        <p>You rolled a {{diceResult}}</p>
    </div>
  </div>

</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'dice',
  data(){
    return{

      'diceResult': null

    }
  },
  methods: {
    rollDice() {
      this.diceResult= Math.floor(Math.random() * 6) + 1;
      eventBus.$emit("dice-rolled",this.diceResult)
    }

  }

}
</script>

<style lang="css" scoped>
</style>


<!-- Show dice on screen and the value -->
