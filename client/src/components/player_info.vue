<template lang="html">
  <div>
    <p v-for="(player,index) in players" :player="player" v-bind:key="index">{{player.name}}</p>
  </div>
</template>

<script>
export default {
  name: 'player_list',
  props: ['players']
}
</script>

<style lang="css" scoped>
</style>
