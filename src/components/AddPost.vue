<template>
  <div class="grid justify-end mr-5 sticky ">
    <button
      @click="openModal = true"
      class="rounded-full bg-neutral-900 my-5 h-16 w-16"
    >
      <svg
        xmlns="http://www.w3.org/2000/svg"
        width="64"
        height="48"
        fill="#fff"
        class="bi bi-plus"
        viewBox="0 0 16 16"
      >
        <path
          d="M8 4a.5.5 0 0 1 .5.5v3h3a.5.5 0 0 1 0 1h-3v3a.5.5 0 0 1-1 0v-3h-3a.5.5 0 0 1 0-1h3v-3A.5.5 0 0 1 8 4z"
        />
      </svg>
    </button>
  </div>

  <div v-if="openModal === true">
    <div
      class="modal fixed z-0 left-0 top-0 flex justify-center items-center p-4 min-h-screen w-full overflow-x-hidden overflow-y-auto bg-neutral-800/90"
    >
      <div class="relative z-10 rounded-lg shadow bg-neutral-900">
        <div
          class="flex items-start justify-between p-4 border-b rounded-t dark:border-gray-600"
        >
          <h3 class="text-xl font-semibold text-gray-900 dark:text-white">
            Create new post
          </h3>
          <button
            @click="openModal = false"
            type="button"
            class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm p-1.5 ml-auto inline-flex items-center dark:hover:bg-gray-600 dark:hover:text-white"
          >
            <svg
              class="w-5 h-5"
              fill="currentColor"
              viewBox="0 0 20 20"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                fill-rule="evenodd"
                d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z"
                clip-rule="evenodd"
              ></path>
            </svg>
          </button>
        </div>
        <div id="post" class="p-6 space-y-6">
          <p
            class="text-lg font-semibold leading-relaxed text-gray-500 dark:text-gray-400"
          >
            User Name
          </p>
          <input
            type="text"
            v-model="newPost.userName"
            placeholder="Ej. User2233"
            class="bg-zinc-700 rounded-full w-full h-8 px-5 pb-1 ring-0 text-white"
          />

          <p
            class="text-lg font-semibold leading-relaxed text-gray-500 dark:text-gray-400"
          >
            Image URL
          </p>
          <input
            type="url"
            pattern="https://.*"
            size="30"
            required
            v-model="newPost.imgUrl"
            placeholder="https://example.com"
            class="bg-zinc-700 rounded-full w-full h-8 px-5 pb-1 ring-0 text-white"
          />
          <p class="text-lg font-semibold text-gray-500 dark:text-gray-400">
            Description
          </p>
          <textarea
            v-model="newPost.description"
            id=""
            cols="30"
            rows="10"
            placeholder="Hello I'm"
            class="bg-zinc-700 rounded-2xl w-full h-32 p-5 ring-0 text-white"
          ></textarea>
        </div>
        <div class="p-3 grid grid-cols-6 gap-2 content-center">
          <div class="cols-2 col-start-3">
            <button
              @click="addPost()"
              type="submit"
              class="text-white bg-blue-600 rounded-full px-8 py-2"
            >
              Post
            </button>
          </div>
          <div class="cols-2 col-start-5">
            <button
              @click="openModal = false"
              class="text-white bg-gray-600 rounded-full px-6 py-2"
            >
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "AddPost",
  data() {
    return {
      openModal: false,
      posts: [],
      newPost: {
        description: "",
        imgUrl: "",
        userName: "",
      },
    };
  },
  mounted() {
    if (localStorage.getItem("posts")) {
      try {
        this.posts = JSON.parse(localStorage.getItem("posts"));
      } catch (e) {
        localStorage.removeItem("posts");
      }
    }
  },
  methods: {
    addPost() {
      if (!this.newPost) {
        return;
      }
      this.posts.push(this.newPost);
      this.$emit("addNewPost", this.newPost);
      this.newPost = {};
      this.savePost();

      this.openModal = false;
    },
    removePost(x) {
      this.posts.splice(x, 1);
      this.savePost();
    },
    savePost() {
      const parsed = JSON.stringify(this.posts);
      localStorage.setItem("posts", parsed);
    },
  },
};
</script>
