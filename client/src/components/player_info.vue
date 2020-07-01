<template lang="html">
  <div>
    <h3 v-for="(player,index) in players" :player="player" v-bind:key="index" >{{player.name}} is {{player.playerColour}}</h3>

    <winning-player v-if="winner" :player="winner"/>
    <button v-if="winner" onClick="window.location.reload();">Play Again?</button>

    <!-- <current-player v-if="currentPlayer" :player="currentPlayer"/> -->
  </div>
</template>

<script>
import Winner from './winScreen.vue';
// import currentPlayer from './currentPlayer.vue'
import { eventBus } from '../main.js'

export default {
  name: 'player_list',
  props: ['players'],
  data(){
    return {
      'winner': null
    } 
  },
  components: {
    'winning-player': Winner,
    // 'current-player': currentPlayer
  },
  mounted(){
    eventBus.$on('player-win', (player) => {
      this.winner = player
    }),
    eventBus.$on('current-player', (player) => {
      this.currentPlayer = player
    })
  }
}
</script>

<style lang="css" scoped>


</style>
