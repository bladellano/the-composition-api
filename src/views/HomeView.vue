<template>
  <div>
    <h1>Home</h1>
    <PostList v-if="showPosts" :posts="posts" />
    <div v-if="error">{{ error }}</div>

    <div v-if="posts.length">
      <button @click="showPosts = !showPosts">toggle posts</button>
    </div>
    <div v-else>Loading...</div>

    <button @click="posts.pop()">delete a post</button>
  </div>
</template>

<script>
import PostList from "../components/PostList";

import getPosts from "../composables/getPosts";

export default {
  name: "Home",
  components: { PostList },

  setup() {

    const { posts, showPosts, error, load } = getPosts();

    load();

    return { posts, showPosts, error };
  },
};
</script>

<style>
</style>