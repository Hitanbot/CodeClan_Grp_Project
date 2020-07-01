<template>
  <div id="app">

    <h2 id="title">Snakes and Ladders</h2>

    <player-info id="players" :players="players"/>

    <game-board id="game-board" :players='players'></game-board>

 </div>
</template>

<script>
import PlayerInfo from './components/player_info.vue'
import GameBoard from './components/GameBoard.vue';

export default {
  name: 'App',
  data(){
    return{
      'players':[{name:'Dave',position:[9,0],playerColour:"red",offset:[10,-10]},
      {name:'Ralph',position:[9,0],playerColour:"blue",offset:[-10,10]},
      // {name:'Joe',position:[9,0],playerColour:"pink",offset:[10,10]},
      // {name:'Fred',position:[9,0],playerColour:"yellow",offset:[-10,-10]}

    ],
      'current_player':null
    }
  },
  components: {
    "game-board":GameBoard, 
    "player-info": PlayerInfo,
  },
  mounted(){

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


/* #game-board {
  position: absolute;
  max-width:26.54%;
  height: auto;
  left: 450px;
  align-self: flex-end;
  flex-flow: column-reverse;
  opacity: 0.4;
} */


#players {
  position: absolute;
  max-width: 20%;
  height: auto;
  left: 90px;
  top: 90px;
  border: 3px red dotted;
}


.square{

}

.player{

}



</style>
