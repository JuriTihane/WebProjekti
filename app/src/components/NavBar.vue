<template>
  <div id="navigation">
    <button @click="show = true" > Symbol </button>
      <ul v-if="show">
        <li>Whats new</li>
        <li>Problems</li>
        <li>Log In</li>
      </ul>
  </div>
</template>

<script>
export default {
    name: 'categories',
    data () {
      return {
        show : false,
      }
    }

}
</script>

<style>
  #navigation {
    float: right;
  }

  li {
    text-decoration: none;
  }
</style>