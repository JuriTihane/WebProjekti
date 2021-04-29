<template>
  <div id="mainWindow" >
    <Browse authors = {{authors}} questions = {{questions}} > </Browse>
    
  </div>
  
</template>

<script>
import Browse from './Browse.vue'

export default {
  
  name: 'Main',
  components: {
    Browse
  },
  props: {
    
  },
  data () {
    return {
      
        authors: [
            
              {author: 'Matti'},
              {author: 'Maija'},
        ],
        questions: [
              {question: 'What is namespace in C++'},
              {question: 'How to filter through an array in Javascript'},
        ]
        }
      }
    }
  

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
