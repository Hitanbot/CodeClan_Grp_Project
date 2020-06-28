<template lang="html">

  <p></p>


</template>

<script>
export default {
  name: 'rules',
  props: ['PlayerPosition']
}



}

methods: {

  movePlayer: function(player){
    if PlayerPosition = [ladderTile]
      [goToLadderTop];
    else if {
      PlayerPosition = [snakeTile]
      [goToSnakeTail]};
    else if PlayerPosition = [endTile]
      [winGame]
      else [otherPlayerTurn]
      }
    },

    mounted(){
      this.movePlayer();

      eventBus.$on("dice-rolled", player => (this.movePlayer = player));
    }
  }



</script>

<style lang="css" scoped>
</style>
