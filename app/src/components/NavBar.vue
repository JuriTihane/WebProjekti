<template>
  <div id="navigation">
    <ul>
      <NavBarItem text="Forum" link=""></NavBarItem>
      <NavBarItem text="Browse" v-on:click="$emit('func')"  ></NavBarItem>
      <NavBarItem text="Ask"></NavBarItem>
      <NavBarItem text="Log In" dropdownItems=navBarContent.userAction></NavBarItem>
      <SearchBar/>
    </ul>
  </div>
</template>

<script>
import NavBarItem from './NavBarItem.vue'
import SearchBar from './SearchBar.vue'

export default {
  components: {
    'NavBarItem': NavBarItem,
    SearchBar
  },
  name: 'categories',
  props: {
    func: Function,
    x : Boolean
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

<style scoped>
ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
  display: flex;
  background-color: green;
  justify-content: space-around;
  height: 3rem;
}
</style>