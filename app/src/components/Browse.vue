<template>
  <div>
    <SearchBar/>
    <ul id="ul_post" v-if="posts && posts.length">
      <li id="li_post" v-for="post of posts" v-bind:key="post" v-on:click="post_open(); isHidden = !isHidden" v-bind:class="{ active: isActive }">
        <div id="div_post">
          <p id="p_post_title"><strong>{{post.title}}</strong></p>
          <p id="p_post_content" v-if="!isHidden">{{post.content}}</p>
          <p id="p_post_comments" v-if="!isHidden">{{post.comments}}</p>
        </div>
      </li>
    </ul>

    <ul v-if="errors && errors.length">
      <li v-for="error of errors" v-bind:key="error">
        {{error.message}}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import SearchBar from './SearchBar'

export default {
  name: 'Browse',
  components: {
    SearchBar
  },
  data() {
    return {
      posts: [],
      errors: [],
      isHidden: true,
      isActive: false
    }
  },

  methods: {
    post_open: function () {
      this.isActive = this.isActive === false;
    },
    // Fetches post every 1 second, trigger in created()
    async update() {
      try {
        console.log("UUU")
        const response = await axios.get(`http://localhost:3000/json/`)
        this.posts = response.data
      } catch (e) {
        this.errors.push(e)
      }
    }
  },

  // Fetches posts when the component is created.
  async created() {
    this.interval = setInterval(() => this.update(), 1000);
    try {
      const response = await axios.get(`http://localhost:3000/json/`)
      this.posts = response.data
    } catch (e) {
      this.errors.push(e)
    }
  }
}
</script>

<style>
.active {
  height: 300px;
}

.active div p {
  vertical-align: bottom;
}

#div_post {
  width: 100%;
}

#ul_post {
  border: 1px solid black;
  padding: 0;
}

#li_post {
  border: 1px solid black;
  margin-bottom: 10px;
}

#p_post_content {
  width: 100%;
  text-align: left;
}
</style>