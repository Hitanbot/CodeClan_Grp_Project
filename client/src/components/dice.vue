<template lang="html">
  <div>
    <p id="placeholder">Something here</p>
    <button id="button" v-on:click="rollDice" type="button">Roll Dice</button>
  </div>
</template>

<script>
export default {
  name: 'dice',
  data(){
    return{
      sides: 6,
      rolledNum: null
    }
  },
  methods: {
    rollDice() {
      var randomNumber = Math.floor(Math.random() * this.sides) + 1;
      this.rolledNum = randomNumber
      return randomNumber;

    }
  }
}
</script>

<style lang="css" scoped>
</style>


<!-- Show dice on screen and the value -->
