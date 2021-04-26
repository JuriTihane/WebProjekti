<template>
  <div id="navigation">
      <ul>
        <NavBarItem text="Forum" ></NavBarItem>
        <NavBarItem text="dsda" > </NavBarItem>
        <NavBarItem text="Log In" > </NavBarItem>
        <SearchBar  />
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
    data () {
      return {
        show : false,
      }
    }

}
</script>

<style>
   ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    display: flex;
    background-color: green;
    justify-content:space-around;
    height: 3rem;
  }

  
</style>