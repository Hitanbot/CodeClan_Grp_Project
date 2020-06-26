<template>
  <div id="app">
    
    <game-board></game-board>
  </div>
</template>

<script>
import GameBoard from './components/GameBoard.vue'

export default {
  name: 'App',
  components: {
    "game-board":GameBoard
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
