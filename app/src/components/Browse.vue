<template>
  <div>
    <SearchBar/>
    <ul id="ul_post" v-if="posts && posts.length">
      <li id="li_post" v-for="post of posts" v-bind:key="post" @click.prevent="activePost = post">
        <div id="div_post">
          <p id="p_post_title"><strong>{{post.title}}</strong></p>
          <p :class="['active',{ 'seens' : !post.seen, 'selected': post === activePost}]" id="p_post_content">{{post.content}}</p>
          <p :class="['active',{ 'seens' : !post.seen, 'selected': post === activePost}]" id="p_post_comments_title"><strong>Comments</strong></p>
          <button v-on:click="sendComment(); update()" :class="['active',{ 'seens' : !post.seen, 'selected': post === activePost}]" id="button_comments">Add comment</button>
          <input id="input_comment" type="text" :class="['active',{ 'seens' : !post.seen, 'selected': post === activePost}]" v-model="comment"/>
          <p :class="['active',{ 'seens' : !post.seen, 'selected': post === activePost}]" id="p_post_comments">{{post.comments}}</p>
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
      activePost: null,
      comment: '',
      referenceID: ''
    }
  },

  methods: {
    async sendComment() {
      try {
        console.log("COMMMEEEENT" + this.comment)
        await axios.post(`http://localhost:3000/postComment/`, {
          id: 0,
          author: "author0",
          content: this.comment
        })
      } catch (e) {
        this.errors.push(e)
      }
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
    //this.interval = setInterval(() => this.update(), 10000);
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
#p_post_content.active.seens.selected {
  display: block;
}

#p_post_comments_title.active.seens.selected {
  display: block;
}

#button_comments.active.seens.selected {
  display: initial;
}

#input_comment.active.seens.selected {
  display: block;
}

#p_post_comments.active.seens.selected {
  display: block;
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
  display: none;
}

#p_post_comments {
  display: none;
}

#button_comments {
  display: none;
}

#input_comment {
  display: none;
  margin-left: auto;
  margin-right: auto;
}

#p_post_comments_title {
  display: none;
}
</style>