<template lang="html">
  <div>
    <h3 v-for="(player,index) in players" :player="player" v-bind:key="index" >{{player.name}} is {{player.playerColour}}</h3>
  
    <winning-player v-if="winner" :player="winner"/>
  </div>
</template>

<script>
import Winner from './winScreen.vue';
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
    'winning-player': Winner
  },
  mounted(){
    eventBus.$on('player-win', (player) => {
      this.winner = player
    })
  }
}
</script>

<style lang="css" scoped>


</style>
