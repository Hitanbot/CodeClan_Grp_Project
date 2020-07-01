<template lang="html">
  <form @submit="handleFormSubmit">
    <h2>Add a Player</h2>
    <div class="formWrap">
      <label for="playername">Player Name: </label>
      <input type="text" id="playername" v-model="name" />
    </div>

    <input type="submit" value="Add Player" id="saveplayer">
  </form>
</template>

<script>

import {eventBus} from '../main.js';

export default {
  name: 'added_player',
  data() {
    return {
      'name': "",
      'playerPosition': 0,
      'isTurn': false
    } 
  },
  methods: {
    handleFormSubmit(event) {
      event.preventDefault();
      const newPlayer = {
        name: this.name,
        playerPosition: this.playerPosition,
        isTurn: this.isTurn
      }
      eventBus.$emit('new-player', newPlayer)
    }
  }

}
</script>

<style lang="css" scoped>
</style>
