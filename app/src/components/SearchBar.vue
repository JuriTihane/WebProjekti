<template>

  <div class="input-wrapper">
    <input type="text" placeholder="Searchbox"/>
    <button id="button_search">Search</button>
  </div>


</template>

<script>
export default {}
</script>

<style>
#button_search {
  height: 34px;
  width: 10%;
}

input {
  width: 90%;
  font-size: 1.5rem;
  margin: 5px;
}

.input-wrapper {
  width: 100%;
  display: flex;
  align-items: center;
}
</style>