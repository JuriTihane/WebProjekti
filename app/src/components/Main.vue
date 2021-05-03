<template>
  <div id="mainWindow">
    <Browse></Browse>

  </div>

</template>

<script>
import Browse from './Browse.vue'

export default {

  name: 'Main',
  components: {
    Browse
  },
  props: {}
}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
