<template>
  <div>
    <NavBar v-bind="x" @func="() => x = !x" />
    <Browse v-show="!x"  />
    
  </div>
</template>

<script>
import Browse from './components/Browse.vue'
import NavBar from './components/NavBar.vue'

export default {
  name: 'App',
  components: {
    Browse,
    NavBar
  },
  data() {
    return {
      
      x : true,
      
      

    }
  },
  methods: {
    func: () => {
      
      // eslint-disable-next-line no-unused-vars
      
      
    }
  }
}


</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body {
  background-color: white;
  margin: 0;
}

</style>
