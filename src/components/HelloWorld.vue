<template>
  <div class="hello">
    <input v-model="postText"
    type="text"
    id="blogInput">
    <button @click="postBlog"> Click me to post! </button>
    <!-- v-for loop for each blog post -->
    <div
    v-for="post in blogPosts" 
    :key="post.postId">
    {{post.postId}}
    <h2>{{post[1]}}</h2>
    <input v-model="updateText"
    type="text"
    id="blogEdit">
    <button @click="editPost">Edit post</button>
    <button @click="deletePost(post.postId)"> Delete post</button>
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
  },
  methods: {
    getPost(){
      axios.request({
        url : "http://127.0.0.1:5000/api/blog_posting",
        method : "GET"
      }).then((response)=>{
        this.blogPosts = response.data;
      }).catch((error=>{
        console.log(error);
      }))
    },
    postBlog(){
      axios.request({
        url : "http://127.0.0.1:5000/api/blog_posting",
        method : "POST",
        data : {
          postText : this.postText
        }
      }).then(()=>{
        this.getPost(); 
      }).catch((error)=>{
        console.log(error);
      })
    },
    deletePost(id){
      axios.request({
        url : "http://127.0.0.1:5000/api/blog_posting",
        method : "DELETE",
        data: {
          postId : id
        }
      }).then((response)=>{
        console.log(response);
      }).catch((error)=>{
        console.log(error);
      })
    },
    editPost(){
      axios.request({
        url : "http://127.0.0.1:5000/api/blog_posting",
        method : "PATCH",
        data : {
          postText : this.postText,
          postId : this.postId
        },
        headers: {
          "Content-Type" : "application/json"
        }
      }).then(()=>{
        this.getPost();
      }).catch((error)=>{
        console.log(error);
      })
    },    
  },
  mounted() {
    this.getPost()
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
