<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
      <div>
          <div class="post" v-for="post in posts" :key="post.id">
              <h3>Title: {{ post.title }}</h3>
              <p>Description: {{ post.body }}</p>
          </div>
      </div>
  </div>
</template>

<script>
    import axios from 'axios'

    export default {
        name: 'HelloWorld',
        props: {
            msg: String
        },
        data () {
            return {
                posts: []
            }
        },
        mounted() {
            var self = this;
            axios.get('https://jsonplaceholder.typicode.com/posts')
                .then (function (res) {
                    self.posts = res.data;
                    console.log('Data: ', res.data);
                })
                .catch (function (error) {
                    console.log('Error: ', error);
                })
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .post {
        background: grey;
        margin-bottom:  20px;
        padding: 10px 20px;
    }
    h3 {
        text-align: left;
    }
    p {
        text-align: left;
    }
</style>
