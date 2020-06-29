<template lang="html">
  <div onload= "gameArea.start">
    <canvas id="c" width = "500" height="500"> </canvas>
    <p>gameboard maybe?</p>
    <!-- <button v-on:click="drawBoard()">rect</button> -->
    <dice></dice>
  </div>

</template>

<script>

import {eventBus} from '../main.js'
import dice from './dice.vue'

export default {
  name: 'game-board',
  data(){
    return{
      'current_player': 0,
      'vueCanvas':null,
      'sqr_of_tiles':10,
      'boardOptions':{
        width:50,
        height:50,
        x:0,
        y:0,
        fill:"green"
      }

    }

  },
  props: ['players'],
  components: {
    'dice': dice
  },
  methods:{

    updateCurrentPlayer(){
      if (this.current_player === this.players.length-1){
        this.current_player = 0
      }
      else {
        this.current_player = this.current_player + 1
      }
    },

    calculateMove(roll, player_index){
      for (let i = roll ; i>0 ; i--){
        if (this.players[player_index].position[0]== 0 && this.players[player_index].position[1] == 0){
          // win
        }
        else{
          if (this.players[player_index].position[0]%2 == 1){
            if (this.players[player_index].position[1] == 9){
              this.players[player_index].position[0]-=1
            }
            else{
              this.players[player_index].position[1]+=1
            }
          }
          else{

            if (this.players[player_index].position[1] == 0){
              this.players[player_index].position[0]-=1
            }
            else{
              this.players[player_index].position[1]-=1
            }
          }
        }
      }},

    drawRect() {
    // clear canvas
    // this.vueCanvas.clearRect(0, 0, 500, 500);

    // draw rect
    this.vueCanvas.beginPath();

    this.vueCanvas.rect(this.boardOptions.x, this.boardOptions.y, this.boardOptions.width, this.boardOptions.height);
    this.vueCanvas.fillStyle = this.boardOptions.fill;
    this.vueCanvas.fill()
    this.vueCanvas.stroke();
    console.log(this.vueCanvas);
  },

  drawPlayer(player) {


    // draw player
    this.vueCanvas.beginPath();

    this.vueCanvas.arc((this.boardOptions.x+25) , (this.boardOptions.y+25), 5, 0, 2 * Math.PI);
    this.vueCanvas.fillStyle = player.playerColour;
    this.vueCanvas.fill()
    this.vueCanvas.stroke();
    console.log(this.vueCanvas);
  },

  drawBoard(){
    // make this constantly redrawing so that it registers changes and can be animated
    this.vueCanvas.clearRect(0, 0, 500, 500);
    for ( let i = 0 ; i < this.sqr_of_tiles; i++){
      for ( let j = 0 ; j < this.sqr_of_tiles; j++){
        if ((i+j)%2 == 0){
          this.boardOptions.fill="green"
        }
        else{
          this.boardOptions.fill="darkgreen"
        }
        console.log(this.boardOptions);


        this.boardOptions.x=j*50;
        this.boardOptions.y=i*50;


        this.drawRect();
        this.players.forEach((player) => {
          if (player.position[0]==i && player.position[1]==j){
            this.drawPlayer(player);
          }


        });

    }
  }
  },

  },
  mounted(){
    const c = document.getElementById("c");
    const ctx = c.getContext("2d");
    this.vueCanvas = ctx;
    this.drawBoard();
    eventBus.$on("dice-rolled", (roll) => {
      this.calculateMove(roll, this.current_player);
      this.updateCurrentPlayer()
      this.drawBoard();
    });},
}
</script>

<style lang="css" scoped>
canvas{
  border: 5px solid black;
}
</style>
