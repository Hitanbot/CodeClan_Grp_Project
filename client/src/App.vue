<template>
  <div id="app">
  <!-- <div> -->
<h2 id="title">Snakes and Ladders</h2>
<!-- </div> -->

    <img src="./assets/game_board.jpg" id="board">
    <img src="./assets/dice.jpg" id="dice">
    <img src="./assets/players.jpg" id="players">

</div>
</template>

<script>


export default {
  name: 'App',
  components: {

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
  background-image: linear-gradient(to right, lime , green);
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
