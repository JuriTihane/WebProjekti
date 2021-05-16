<template>
  <div id="div_test">
    <SearchBar/>
    <ul id="ul_post" v-if="posts && posts.length">
      <li id="li_post" v-for="post of posts" v-bind:key="post" @click.prevent="activePost = post">
        <div id="div_post">
          <p id="p_post_title"><strong>{{post.title}}</strong></p>
          <p :class="['active',{ 'seens' : !post.seen, 'selected': post === activePost}]" id="p_post_content">{{post.content}}</p>
          <p :class="['active',{ 'seens' : !post.seen, 'selected': post === activePost}]" id="p_post_comments_title"><strong>Comments</strong></p>
          <button v-on:click="sendComment(); update()" :class="['active',{ 'seens' : !post.seen, 'selected': post === activePost}]" id="button_comments">Add comment</button>
          <input id="input_comment" type="text" :class="['active',{ 'seens' : !post.seen, 'selected': post === activePost}]" v-model="comment"/>

          <div v-for="comment1 in post.comments" :key="comment1" id="div_post_comment" :class="['active',{ 'seens' : !post.seen, 'selected': post === activePost}]">
            <p v-if="comment1.date" v-text="'Time added: ' + comment1.date"></p>
            <p v-if="comment1.author" v-text="'Author: ' + comment1.author" id="p_post_comments_author"></p>
            <p v-if="comment1.content" v-text="'Comment: ' + comment1.content" id="p_post_comments_content"></p>
            <p v-else v-text="'Content missing...'"></p>
          </div>

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
      referenceTitle: ''
    }
  },

  methods: {
    async sendComment() {
      try {
        console.log("COMMMEEEENT" + this.comment)
        await axios.post(`http://localhost:3000/postComment/`, {
          referenceTitle: this.activePost.title,
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
#div_test {
  padding-left: 30px;
  padding-right: 30px;
}

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

#div_post_comment.active.seens.selected {
  display: block;
}

#p_post_title {
  width: 50%;
}

#p_post_content {
  width: 98%;
}

#p_post_comments_title {
  width: 50%;
}

#div_post {
  width: 98%;
  margin-left: 10px;
}

#ul_post {
  padding: 0;
  list-style-type: none;
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

#button_comments {
  display: none;
}

#input_comment {
  display: none;
  margin-right: auto;
}

#div_post_comment {
  display: none;
  border-top: 1px solid black;
  border-left: 1px solid black;
  border-right: 1px solid black;
  padding-left: 20px;
}

#p_post_comments_content {
  margin-bottom: 0;
}

#p_post_comments_title {
  display: none;
}
</style>