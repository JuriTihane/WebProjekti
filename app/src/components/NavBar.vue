<template>
  <div id="navigation">
    <ul class="navigation-bar" >
      <NavBarItem text="Forum" ></NavBarItem>
      <NavBarItem text="Browse" v-on:click="$emit('funcBrowse')"  ></NavBarItem>
      <NavBarItem text="Ask" v-on:click="$emit('funcAsk')"></NavBarItem>
      <NavBarItem text="Log In" v-on:click="$emit('funcLogin')" ></NavBarItem>
      
    </ul>
  </div>
</template>

<script>
import NavBarItem from './NavBarItem.vue'


export default {
  components: {
    'NavBarItem': NavBarItem,
    
  },
  name: 'categories',
  props: {
    

  },
  data() {
    return {
      
      navBarContent: {
        userAction: [
          {item: "Log In"},
          {item: "Sign Up"}
        ],
      }
    }
  },
  methods: {

    
    
  }
  
  

}
</script>

<style >
.navigation-bar {
  list-style-type: none;
  margin: 0;
  padding: 0;
  display: flex;
  background-color: green;
  justify-content: space-around;
  height: 3rem;
  font-family: Arial;
  font-size: 1.4em;
}
</style>