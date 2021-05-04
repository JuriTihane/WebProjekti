<template>
  <li v-on:click="$emit('showItems')" >
    <a>{{ text }}</a>
    <p class="dropDownItems"></p>
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
li a {
  text-decoration: none;
  color: white;

}

li {
  width: 100%;
  display: flex;
  justify-content: center;
  align-items: center;

}

li:hover {
  background-color: tomato;
}


</style>