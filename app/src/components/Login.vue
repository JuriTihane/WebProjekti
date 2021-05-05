<template>
  <div >

      <div class="login-site" >
        
        
        <button  @click="() => {showLogin = false
           showSignUp = true }" >Sign Up
           </button>
        <button  @click="() => {showLogIn = true
          showSignUp = false} " >Log In</button>

        <h3 v-show="showSignUp" >Email</h3>
        <input v-show="showSignUp" type="text">
        <h3>Username</h3>
        <input type="text" placeholder="">
        <h3>Password</h3>
        <input type="text" placeholder="">
        <button v-show="showSignUp">Sign Up</button>
        <button v-show="!showSignUp" >Log In</button>
      </div>

      
      
  </div>
  
</template>

<script>
export default {
    name: 'Login',
    data () {
      return {
        showLogIn: false,
        showSignUp: false
      }

    }
}
</script>

<style>

  .login-site {
    font-family: Arial;
    font-size: 1em;
    align-items: center;
  }

  .login-site button {
    padding: 5px;
  }

</style>