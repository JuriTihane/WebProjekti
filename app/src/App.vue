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
}


</script>

<style>




body {
  background-color: white;
  margin: 0;
}

</style>
