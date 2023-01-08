<template>
  <div v-if="allPost != null">
    <div class="px-4">
      <div
        v-for="post in allPost"
        :key="post.id"
        class="rounded-xl border-slate-700 my-10 bg-black text-white"
      >
        <div class="m-3">{{ post.userName }}</div>
        <div class="bg-neutral-600 bg-no-repeat bg-cover bg-center bg-fixed">
          <img :src="post.imgUrl" alt="" class="" />
        </div>
        <div class="px-4">
          <div class="">
            <ul class="flex gap-4">
              <li>like</li>
              <li>comment</li>
              <li>send</li>
            </ul>
          </div>
          
          <div class="my-4">user: {{ post.description }}</div>
        </div>
      </div>
    </div>
  </div>
  <div v-else class="text-white">
    No posts found
  </div>
</template>

<script>
export default {
  name: "PostCard",
  data() {
    return {
      allPost: [],
    };
  },
  props: {
    data: Object,
  },
  watch: {
    data: function (val) {
      if (val) {
        if (this.allPost == null) {
          this.allPost = [];
        }
        this.allPost.push(val);
      }
    },
  },
  computed: {
    getPost() {
      return JSON.parse(localStorage.getItem("posts"));
    },
  },
  mounted() {
    this.allPost = JSON.parse(localStorage.getItem("posts"));
    console.log(this.allPost);
  },
};
</script>
