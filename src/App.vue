<template>
  <div>
    <Navbar></Navbar>
    <PostCard :data="post"></PostCard>
    <AddPost @addNewPost="newPostData"></AddPost>
  </div>
</template>

<script>
import "./assets/tailwind.css";
import Navbar from "./components/Navbar.vue";
import AddPost from "./components/AddPost.vue";
import PostCard from "./components/PostCard.vue";

export default {
  name: "App",
  components: { Navbar, AddPost, PostCard },
  data() {
    return {
      post: {},
    };
  },
  methods: {
    newPostData(value) {
      console.log(value);
      this.post = value;
    },
  },
};
</script>

<style>
body {
  background-color: rgb(38 39 38);
}
</style>
