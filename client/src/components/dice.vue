<template lang="html">
  <p>{{diceResult}}</p>
</template>

<script>
export default {
  name: 'dice',
  data(){
    return(
<<<<<<< HEAD
      'diceResult': rollDice
=======
      'diceResult': rollDice()
>>>>>>> develop
    )
  },
  methods: {
    rollDice() {
      return Math.floor(Math.random() * 6) + 1;
    }
<<<<<<< HEAD
  }
=======
}

>>>>>>> develop
}
</script>

<style lang="css" scoped>
</style>


<!-- Show dice on screen and the value -->
