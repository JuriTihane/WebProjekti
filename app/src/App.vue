<template>
  <div>
    <NavBar v-bind="xBrowse" 
    @funcBrowse="() => {
      xBrowse = !xBrowse
    }" 
    @funcAsk="() => {
      xAsk = !xAsk
    }"
    @funcLogin="() => {
      xLogin = !xLogin
    }"
     />

    <Browse v-show="!xBrowse"  />
    <Ask v-show="!xAsk" />
    <Login v-show="!xLogin" />
    
  </div>
</template>

<script>
import Browse from './components/Browse.vue'
import Ask from './components/Ask.vue'
import Login from './components/Login.vue'
import NavBar from './components/NavBar.vue'

export default {
  name: 'App',
  components: {
    Browse,
    NavBar,
    Login,
    Ask
  },
  data() {
    return {
      
      xBrowse : true,
      xAsk : true,
      xLogin : true
      

    }
  },
  methods: {
    func: () => {
      
      // eslint-disable-next-line no-unused-vars
      console.log("Funciin tuli kutsu")
      
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
