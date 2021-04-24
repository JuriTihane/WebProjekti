<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <NavBar  />
    
  </div>
  
</template>

<script>
import NavBar from './NavBar.vue'

export default {
  components: { NavBar },
  name: 'Main',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
