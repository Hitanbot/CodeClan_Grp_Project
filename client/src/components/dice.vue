<template lang="html">
  <div>
    <button v-on:click="rollDice()">roll dice</button>
    <div v-if="diceResult">
        <p>{{diceResult}}</p>
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
