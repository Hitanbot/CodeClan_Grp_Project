<template lang="html">
  <div>
    <p v-for="player in players" :player="player">{{player.name}}</p>
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
