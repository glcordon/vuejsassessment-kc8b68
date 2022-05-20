<script>
// 1. Create a 2 page site with Vue.js
//SPA?
//Do I have acces to Vue Router?
//I may move to my local machine to get access to vue Router
import Vue from 'vue';
// import router from "./router"
//

// 2. On the home page list out posts from https://jsonplaceholder.typicode.com/
//Do I use fetch or axios 🤔
// 3. Each post should link to a dedicated page for just that post (just like a blog)
// 4. Include an edit button and form on the dedicated post page that allows admins to edit it (not actual possible to edit post resource on https://jsonplaceholder.typicode.com/) but you can fake it however you'd like
// 5. Use the Options API at least once (but also feel free to use CAPI if desired)
// 6. Feel free to work directly in this StackBlitz project or start your own project locally and share it via Github
// import Posts from '@/components/Posts';
export default {
  // components: {
  //   Posts,
  // },
  data() {
    return {
      posts: [],
    };
  },
  mounted() {
    fetch('https://jsonplaceholder.typicode.com/posts')
      .then((res) => res.json())
      .then((data) => (this.posts = data))
      .catch((err) => console.log(err.message));
  },
  methods() {},
};
</script>

<template>
  <!-- <Posts v-for="post in posts" :key="post.id" class="posts" :title="post.title">
    {{ post.title }}
  </Posts> -->
  <div v-for="post in posts" :key="post.id" class="posts">
    <div id="post_header">
      <h2>
        {{ post.title }}
      </h2>
    </div>
    <div class="post_body">
      {{ post.body }}
    </div>
    <div class="post_button">
      <a :post-id="post.id" class="btn btn-primary">View</a>
    </div>
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.posts {
  padding: 10px;
  border: 1px solid #ccc;
  margin: 10px 0;
}
.posts #post_header h2 {
  font-size: 14px;
  font-weight: 500;
  text-decoration: underline;
  background: #ccc;
  padding: 10px 5px;
  border: 1px solid #333;
}
.btn {
  display: inline-block;
  margin-bottom: 0;
  font-weight: 400;
  text-align: center;
  white-space: nowrap;
  vertical-align: middle;
  -ms-touch-action: manipulation;
  touch-action: manipulation;
  cursor: pointer;
  background-image: none;
  border: 1px solid transparent;
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  border-radius: 4px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}
.btn.btn-primary {
  color: #fff;
  background-color: #337ab7;
  border-color: #2e6da4;
}
</style>
