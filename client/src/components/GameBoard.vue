<template lang="html">
  <div onload= "gameArea.start">
    <canvas id="c" width = "500" height="500"> </canvas>
    <p>gameboard maybe?</p>
    <button v-on:click="drawRect()">rect</button>
  </div>

</template>

<script>




export default {
  name: 'game-board',
  data(){
    return{
      'vueCanvas':null
      // 'sqr_of_tiles':5

    }

  },
  methods:{
    drawRect() {
    // clear canvas
    this.vueCanvas.clearRect(0, 0, 400, 200);

    // draw rect
    this.vueCanvas.beginPath();

    this.vueCanvas.rect(0, 0, 100, 100);
    this.vueCanvas.fillStyle = 'green';
    this.vueCanvas.fill()
    this.vueCanvas.stroke();
    console.log(this.vueCanvas);
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
