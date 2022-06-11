<template>
  <div class="hello">
    <input v-model="inputPost"
    type="text"
    id="blogInput">
    <button @click="postText"> Click me to post! </button>
    <div
    v-for="post in blogPosts" 
    :key="post.postId">
    <h2>{{post.postId}}</h2>
    <button @click="editPost">Edit post</button>
    <button @click="deletePost"> Delete post</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'HelloWorld',
  data(){
    return{
      blogPosts: []
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
