<template>
  <div id="navigation">
      <ul>
        <NavBarItem text="Foorumi" ></NavBarItem>
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
  #navigation ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    width: 200px;
    background-color: #f1f1f1;
  }

  li {
    text-decoration: none;
    
  }
</style>