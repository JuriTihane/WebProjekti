<template>
  
  <NavBar  />
</template>

<script>
//import Main from './components/Main.vue'
import NavBar from './components/NavBar.vue'


export default {
  name: 'App',
  components: {
    
    NavBar
  },
  data () {
    return {
      content: [
        {
          id: 1,
          text: "Foorumi"
        }
      ]
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
  margin-top: 60px;
}
body {
    background-color: white;
  }
</style>
