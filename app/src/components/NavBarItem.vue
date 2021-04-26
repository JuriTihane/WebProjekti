<template>
  <li class="item">
    <a href="">{{text}}</a>
  </li>
</template>

<script>
export default {
    name: 'NavBarItem',
    props: {
        text: String,
        
    }
}
</script>

<style>
    #item li a {
        display: inline;
        padding: 15px;
        text-decoration: none;
    }
    #item li a.active {
        background-color: indigo;
        color: red;
    }
</style>