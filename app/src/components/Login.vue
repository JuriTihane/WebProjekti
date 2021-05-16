<template>
  <div>

    <div class="login-site">


      <button @click="() => {showLogin = false
           showSignUp = true }">Sign Up
      </button>
      <button @click="() => {showLogIn = true
          showSignUp = false} ">Log In
      </button>

      <form @submit.prevent="registerUser" v-show="showSignUp">
        <h2 v-if="registrationResponse === 'Registration was successful'" v-text="registrationResponse" style="color: green"></h2>
        <h2 v-else v-text="registrationResponse" style="color: red"></h2>
        <h3>Email</h3>
        <input type="email" id="email" placeholder="Email" v-model="register.email" required>
        <h3>Username</h3>
        <input type="text" placeholder="Username" id="name" v-model="register.name" required>
        <h3>Password</h3>
        <input type="password" placeholder="Password" id="password" v-model="register.password">
        <button type="submit">Sign Up</button>
      </form>

      <form @submit.prevent="loginUser" v-show="!showSignUp">
        <h2 v-if="loginResponse === 'Login successful'" v-text="loginResponse" style="color: green"></h2>
        <h2 v-if="loginResponse === 'Login error, check your email and password and try again'" v-text="loginResponse" style="color: red"></h2>
        <h3>Email</h3>
        <input type="email" id="email_login" placeholder="Email" v-model="login.email" required>
        <h3>Password</h3>
        <input type="password" placeholder="Password" id="password_login" v-model="login.password">
        <button type="submit">Log in</button>
      </form>
    </div>


  </div>

</template>

<script>
import axios from "axios";

export default {
  name: 'Login',
  data() {
    return {
      registrationResponse: "",
      loginResponse: "",
      login: {
        email: "",
        password: ""
      },
      register: {
        name: "",
        email: "",
        password: ""
      },
      showLogIn: false,
      showSignUp: false
    }

  },
  methods: {
    async registerUser() {
      this.registrationResponse = ""
      try {
        let response = await axios.post("http://localhost:3000/user/register", this.register);
        let token = response.data.token;
        if (token) {
          localStorage.setItem("jwt", token);
          await this.$router.push("/");
          console.log("Registration Was successful")
          this.registrationResponse = "Registration was successful"
        } else {
          console.log("Something Went Wrong")
          this.registrationResponse = "Something went wrong"
        }
      } catch (err) {
        let error = err.response;
        if (error) {
          console.log("Error", error.data.message)
          this.registrationResponse = error.data.message
        } else {
          console.log("Error", error.data.err.message)
          this.registrationResponse = error.data.err.message
        }
      }
    },
    async loginUser() {
      this.loginResponse = ""
      try {
        let response = await axios.post("http://localhost:3000/user/login", this.login);
        let token = response.data.token;
        localStorage.setItem("jwt", token);
        if (token) {
          console.log("Success", "Login Successful", "success")
          this.loginResponse = "Login successful"
        }
      } catch (err) {
        console.log("Error", "Something Went Wrong", "error")
        this.loginResponse = "Login error, check your email and password and try again"
        console.log(err);
      }
    }
  }
}
</script>

<style>

.login-site {
  font-family: Arial;
  font-size: 1em;
  align-items: center;
  padding-left: 30px;
}

.login-site button {
  padding: 5px;
}

</style>