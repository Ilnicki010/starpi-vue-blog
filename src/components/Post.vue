<template>
  <transition name="slide">
    <router-link :to="'/post/' + this.post.id">
      <div class="itemWrapper">
        <div :style="this.style" class="item"></div>
        <h1>{{this.post.title}}</h1>
        <span>by {{this.post.user.username}}</span>
        <p>{{this.post.short_content}}</p>
        <div class="read-more">+</div>
      </div>
    </router-link>
  </transition>
</template>
<script>
export default {
  name: "Post",
  props: {
    post: {
      type: Object,
      required: true
    }
  },
  data() {
    return {};
  },
  computed: {
    style() {
      if (this.post.cover) {
        return `background-image:url("http://localhost:1337${
          this.post.cover.url
        }")`;
      } else {
        return `background:#42b983`;
      }
    }
  }
};
</script>
<style lang="scss" scoped>
.itemWrapper {
  display: flex;
  flex-direction: column;
  flex: 1;
  justify-content: center;
  align-items: center;
  margin: 20px;
  width: 28vw;
  height: 50vh;
  box-shadow: 0 13px 50px rgba(66, 185, 131, 0.2);
  padding-bottom: 40px;
  border-radius: 4px;
  transition: transform 0.3s ease-in;
  @media screen and (max-width: 600px) {
    min-width: 90vw;
    margin-bottom: 10vh;
  }
  &:hover {
    transform: scale(1.03);
  }
}
.item {
  flex: 1;
  width: 28vw;
  height: 20vh;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
  border-radius: 4px;
  @media screen and (max-width: 600px) {
    min-width: 100%;
  }
}
.read-more {
  flex: 1;
  display: flex;
  width: 30px;
  max-height: 30px;
  border-radius: 60px;
  background: #42b983;
  justify-content: center;
  color: #fff;
  font-weight: 900;
  align-items: center;
  box-shadow: 0 13px 50px rgba(66, 185, 131, 0.3);
  transition: 0.2s ease-in-out;
  margin-top: 15px;
  cursor: pointer;
  &:hover {
    box-shadow: none;
    width: 100px;
  }
}
a {
  text-decoration: none;
  color: #222;
}
.slide-enter-active,
.slide-leave-active {
  transition: margin 0.4s ease-in-out;
}
.slide-enter, .slide-leave-to /* .fade-leave-active below version 2.1.8 */ {
  margin-top: 100vh;
}
</style>