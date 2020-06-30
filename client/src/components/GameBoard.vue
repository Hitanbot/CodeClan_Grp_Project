<template lang="html">
  <div onload= "gameArea.start">
    <canvas id="c" width = "500" height="500"> </canvas>
    <p>gameboard maybe?</p>
    <!-- <button v-on:click="gameLoop()">rect</button> -->
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
      'interval':null,
      'sqr_of_tiles':10,
      'boardOptions':{
        width:50,
        height:50,
        x:0,
        y:0,
        fill:"green"
      },
      'snakeLadderList':[
        {start:[0,5],end:[9,9]},
        {start:[5,5],end:[3,8]},
        {start:[5,8],end:[4,6]},
        {start:[3,8],end:[8,3]}

      ],


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
        let indexY =this.players[player_index].position[0];
        let indexX =this.players[player_index].position[1];

          if (indexY%2 == 1){
            //if at end of row move up
            if (indexX == 9){

              this.players[player_index].position[0]-=1
            }
            else{
              this.players[player_index].position[1]+=1
            }
          }
          else{
            //if at end of row move up
            if (indexX == 0){
              this.players[player_index].position[0]-=1
            }
            else{
              this.players[player_index].position[1]-=1
            }
          }


          // checking if player is on a snake or ladder

        //checking if player has won
          if (this.players[player_index].position[0]== 0 && this.players[player_index].position[1] == 0){
            // win
          }


      }
      this.snkLadderEvent(player_index)


  },

    drawRect() {
    // clear canvas
    // this.vueCanvas.clearRect(0, 0, 500, 500);

    // draw rect
    this.vueCanvas.beginPath();

    this.vueCanvas.rect(this.boardOptions.x, this.boardOptions.y, this.boardOptions.width, this.boardOptions.height);
    this.vueCanvas.fillStyle = this.boardOptions.fill;
    this.vueCanvas.fill()
    this.vueCanvas.stroke();

  },

  drawPlayer(player) {


    // draw player
    this.vueCanvas.beginPath();

    this.vueCanvas.arc((this.boardOptions.x+25+(player.offset[0])) , (this.boardOptions.y+25+(player.offset[1])), 5, 0, 2 * Math.PI);
    this.vueCanvas.fillStyle = player.playerColour;
    this.vueCanvas.fill()
    this.vueCanvas.stroke();

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

  // moveLeft(){}, should modularize for readability
  // moveRight(){},
  // checkWon(){},
  snkLadderEvent(player_index){
    this.snakeLadderList.forEach((snkLad) => {
      if (snkLad.start[0]==this.players[player_index].position[0] && this.players[player_index].position[1] == snkLad.start[1]){
          console.log("hit snake/ladder")
          this.players[player_index].position[0]=snkLad.end[0];
          this.players[player_index].position[1]=snkLad.end[1];
        }

    });
  },
  gameLoop(){
    setInterval(() => {this.drawBoard()},20);
  }

  },
  mounted(){
    const c = document.getElementById("c");
    const ctx = c.getContext("2d");
    this.vueCanvas = ctx;

    this.gameLoop();
    eventBus.$on("dice-rolled", (roll) => {
      this.calculateMove(roll, this.current_player);
      this.updateCurrentPlayer()

    });},
}
</script>

<style lang="css" scoped>
canvas{
  border: 5px solid black;
}
</style>
