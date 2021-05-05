<template>
  <div>
    <NavBar v-bind="xBrowse" 
    @funcBrowse="() => {
      xLogin = false
      xAsk = false
      xBrowse = true
    }" 
    @funcAsk="() => {
      xLogin = false
      xBrowse = false
      xAsk = true
    }"
    @funcLogin="() => {
      xAsk = false
      xBrowse = false
      xLogin = true
      
    }"
     />

    <Browse v-show="xBrowse"  />
    <Ask v-show="xAsk" />
    <Login v-show="xLogin" />
    
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
      
      xBrowse : false,
      xAsk : false,
      xLogin : false
      

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
