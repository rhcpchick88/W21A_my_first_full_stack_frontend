<template>
  <div class="hello">
    <input v-model="blogPost"
    type="text"
    id="blogInput">
    <button @click="postText"> Click me to post! </button>
    <h3>{{posts}}<button @click="editPost">Edit post</button><button @click="deletePost"> Delete post</button></h3>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
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
