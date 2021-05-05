<template>
  <li id="navbaritem" v-on:click="$emit('showItems')" >
    <a>{{ text }}</a>
  </li>
</template>

<script>
export default {
  name: 'NavBarItem',
  props: {
    text: String,
    dropdownItems: Array,
    link: Function,
    x : Boolean
  }
}
</script>

<style>
#navbaritem a {
  text-decoration: none;
  color: white;

}

#navbaritem {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;

}

#navbaritem:hover {
  background-color: tomato;
}


</style>