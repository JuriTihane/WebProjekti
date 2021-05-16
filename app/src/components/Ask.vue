<template>
  <div id="div_ask">
    <h3 v-if="serverResponse.data === 'Same topic / post found'" v-text="serverResponse.data" style="color: red"></h3>
    <h3 v-if="serverResponse.data === 'Post added successfully'" v-text="serverResponse.data" style="color: green"></h3>
    <h3>Title</h3>
    <input type="text" v-model="postTitle" />
    <h3>Topic</h3>
    <input type="text" v-model="postTopic" />
    <h3>Question</h3>
    <input type="text" v-model="postContent" />
    <br/>
    <button v-on:click="postPost">Submit</button>

  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Ask',
  data() {
    return {
      postTitle: '',
      postTopic: '',
      postContent: '',
      serverResponse: '',
      errors: []
    }
  },

  methods: {
    // Pushes posts to the server when called.
    async postPost() {
      this.serverResponse = ''
      try {
        await axios.post(`http://localhost:3000/post/`, {
            id: 0,
            author: "author0",
            topic: this.postTopic,
            title: this.postTitle,
            content: this.postContent
        }).then(response => {
          this.serverResponse = response;
          console.log(response.data)
        })
      } catch (e) {
        this.errors.push(e)
      }
    }
  }
}

</script>

<style scoped>
* {
  font-size: 1em;
  font-family: Arial;
}

#div_ask {
  padding-left: 30px;
}

</style>