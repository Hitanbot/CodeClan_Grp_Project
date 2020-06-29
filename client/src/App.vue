<template>
  <div id="app">
  <!-- <div> -->
<h2 id="title">Snakes and Ladders</h2>
<!-- </div> -->

    <!-- <img src="./assets/game_board.jpg" id="board">
    <img src="./assets/dice.jpg" id="dice">
    <img src="./assets/players.jpg" id="players"> -->
    <game-board :players='players'></game-board>
    <dice></dice>
</div>
</template>

<script>
import GameBoard from './components/GameBoard.vue'
import Dice from './components/dice.vue'
import { eventBus } from './main.js'

export default {
  name: 'App',
  data(){
    return{
      'players':[{name:'dave',position:[9,0],playerColour:"red"},{name:'ralph',position:[9,5],playerColour:"blue"}],
      'current_player':null
    }
  },
  components: {
    "game-board":GameBoard,
    "dice":Dice
  },
  mounted(){
    //pull in player data eventually

    eventBus.$on("dice-rolled", (roll) => {

      for (let i = roll ; i>0 ; i--){
        if (this.players[0].position[0]== 0 && this.players[0].position[1] == 0){
          // win
        }
        else{
        if (this.players[0].position[0]%2 == 1){
          if (this.players[0].position[1] == 9){
            this.players[0].position[0]-=1
          }
          else{
            this.players[0].position[1]+=1
        }
        }
        else{

          if (this.players[0].position[1] == 0){
            this.players[0].position[0]-=1
          }
          else{
            this.players[0].position[1]-=1
          }
        }
      }
         //current_player but just gonna be one of them for now
           console.log(this.players[0].position[1])
           console.log(this.players[0].position[0])

      }


    });
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
