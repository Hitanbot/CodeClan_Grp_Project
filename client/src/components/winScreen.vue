<template lang="html">
  <div>
    <p>The winning player is {{player.name}}!</p>
  </div>
</template>

<script>

export default {
name: 'Winner',
props: ['player']

}
</script>

<style>
</style>
