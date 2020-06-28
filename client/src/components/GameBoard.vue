<template lang="html">
  <div onload= "gameArea.start">
    <canvas id="c" width = "500" height="500"> </canvas>
    <p>gameboard maybe?</p>
    <button v-on:click="drawBoard()">rect</button>
  </div>

</template>

<script>




export default {
  name: 'game-board',
  data(){
    return{
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
  methods:{


    drawRect() {
    // clear canvas
    // this.vueCanvas.clearRect(0, 0, 400, 200);

    // draw rect
    this.vueCanvas.beginPath();

    this.vueCanvas.rect(this.boardOptions.x, this.boardOptions.y, this.boardOptions.width, this.boardOptions.height);
    this.vueCanvas.fillStyle = this.boardOptions.fill;
    this.vueCanvas.fill()
    this.vueCanvas.stroke();
    console.log(this.vueCanvas);
  },

  drawBoard(){
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

    }
  }
  },

  },
  mounted(){
    const c = document.getElementById("c");
    const ctx = c.getContext("2d");
    this.vueCanvas = ctx;
    },
}
</script>

<style lang="css" scoped>
canvas{
  border: 5px solid black;
}
</style>
