<template>
  <div id="app">
  <!-- <div> -->
<h2 id="title">Snakes and Ladders</h2>
<!-- </div> -->

    <!-- <img src="./assets/game_board.jpg" id="board">
    <img src="./assets/dice.jpg" id="dice">
    <img src="./assets/players.jpg" id="players"> -->
    <game-board :players='players'></game-board>
    <!-- <dice></dice> -->
    <winning-player v-if="winner" :player="winner"/>
 </div>
</template>

<script>
import GameBoard from './components/GameBoard.vue';
import Winner from './components/winScreen.vue';
// import Dice from './components/dice.vue'
import { eventBus } from './main.js'

export default {
  name: 'App',
  data(){
    return{
      'players':[{name:'Dave',position:[9,0],playerColour:"red",offset:[10,-10]},
      {name:'Ralph',position:[9,0],playerColour:"blue",offset:[-10,10]},
      {name:'Joe',position:[9,0],playerColour:"pink",offset:[10,10]},
      {name:'Fred',position:[0,2],playerColour:"yellow",offset:[-10,-10]}

    ],
      'current_player':null,
      'winner': null
    }
  },
  components: {
    "game-board":GameBoard,
    "winning-player": Winner,
    // "dice":Dice
  },
  mounted(){
    eventBus.$on('player-win', (player) => {
      this.winner = player
    })
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
  background-image: linear-gradient(to right, silver , white);
  /* margin-top: 60px; */
}

#title {
    background-image: linear-gradient(to right, lime , green);
}


#board {
  position: absolute;
  max-width: 40%;
  height: auto;
  align-self: flex-end;
  flex-flow: column-reverse;
}

#players {
  position: absolute;
  max-width: 20%;
  height: auto;
  left: 136px;
  top: 90px;
}



#dice{
  position: absolute;
  max-width: 10%;
  height: auto;
  left: 200px;
  bottom: 20px;
}


{

}

.square{

}

.player{

}



</style>
