<template lang="html">
  <div>
    <p>The winning player is {{player.name}}!</p>
  </div>
</template>

<script>
// import {eventBus} from '../main.js';

export default {
name: 'Winner',
props: ['player']
// data(){
//   return{
//     'winner': null,
//   }
// },
// mounted(){
//
// }
}
</script>

<style>
</style>
