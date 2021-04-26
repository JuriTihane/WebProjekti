<template>
  <li >
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