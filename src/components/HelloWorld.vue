<template>
  <div class="hello">
      <h1>{{ msg }}</h1>
      <div class="card" v-for="post in posts" :key="post.id">
          <div class="card-content">
              <div class="media">
                  <div class="media-content">
                      <p class="title is-4">Title: {{ post.title }}</p>
                  </div>
              </div>
              <div class="content">
                  <p>Description: {{ post.body }}</p>
              </div>
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

<style scoped>
    p {
        text-align: left;
    }
    .card {
        margin-left: 50px;
        margin-right: 50px;
        margin-bottom: 20px;
    }
    h1 {
        font-size: 30px;
        font-weight: bold;
    }
</style>
