<template>
  <div class="fullPostWrapper">
    <div v-if="this.post.cover" class="image" :style="this.style"></div>
    <h1 class="header">
      {{this.post.title}}
      <span class="author">by {{this.post.user.username}}</span>
    </h1>
    <p class="short">{{this.post.short_content}}</p>
    <p class="content">{{this.post.content}}</p>
  </div>
</template>
<script>
import axios from "axios";
export default {
  name: "FullPost",
  props: ["postId"],

  data() {
    return {
      post: null
    };
  },

  mounted() {
    this.fetchPost();
  },
  computed: {
    style() {
      if (this.post.cover) {
        return `background-image:url("http://localhost:1337${
          this.post.cover.url
        }")`;
      }
    }
  },
  methods: {
    fetchPost() {
      axios.get("http://localhost:1337/posts/" + this.postId).then(response => {
        this.post = response.data;
        console.log(this.post);
      });
    }
  }
};
</script>
<style lang="scss" scoped>
.fullPostWrapper {
  display: flex;
  flex-direction: column;
  flex: 1;
  justify-content: center;
  align-items: center;
}
.image {
  flex: 1;
  width: 90vw;
  height: 40vh;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  border-radius: 4px;
}
.header {
  color: #42b983;
  font-size: 3em;
}
.author {
  font-size: 0.4em;
  opacity: 0.6;
}
.short {
  font-weight: 800;
}
.content {
  padding: 0 100px;
  font-size: 1.2em;
  @media screen and (max-width: 600px) {
    padding: 5px 35px;
  }
}
</style>
