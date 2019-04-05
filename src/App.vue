<template>
  <div id="app">
    <Slide>
      <div id="nav">
        <span>
          <router-link to="/">Blog</router-link>
        </span>
        <span>
          <router-link to="/about">About</router-link>
        </span>
      </div>
    </Slide>
    <div class="content">
      <transition name="fade">
        <router-view/>
      </transition>
    </div>
  </div>
</template>
<script>
import { Slide } from "vue-burger-menu";
export default {
  components: {
    Slide // Register your component
  }
};
</script>
<style lang="scss">
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.content {
  margin-top: 16vh;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: rgba(255, 255, 255, 0.6);
    text-decoration: none;

    margin: 5px;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.3s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
.slide-enter-active,
.slide-leave-active {
  transition: margin 0.3s;
}
.slide-enter, .slide-leave-to /* .fade-leave-active below version 2.1.8 */ {
  margin-top: -50px;
}
//menu
.bm-burger-button {
  position: fixed;
  width: 26px;
  height: 20px;
  left: 36px;
  top: 36px;
  cursor: pointer;
}
.bm-burger-bars {
  background-color: #42b983;
}
.line-style {
  position: absolute;
  height: 20%;
  left: 0;
  right: 0;
}
.cross-style {
  position: absolute;
  top: 12px;
  right: 2px;
  cursor: pointer;
}
.bm-cross {
  background: #bdc3c7;
}
.bm-cross-button {
  height: 24px;
  width: 24px;
}
.bm-menu {
  height: 100%; /* 100% Full-height */
  width: 0; /* 0 width - change this with JavaScript */
  position: fixed; /* Stay in place */
  z-index: 1000; /* Stay on top */
  top: 0;
  left: 0;
  background-color: #123022; /* Black*/
  overflow-x: hidden; /* Disable horizontal scroll */
  padding-top: 60px; /* Place content 60px from the top */
  transition: 0.5s; /*0.5 second transition effect to slide in the sidenav*/
}

.bm-overlay {
  transition: background-color 1s linear;
  background: rgba(66, 185, 131, 0.1);
}
.bm-item-list {
  color: #fff;
  margin-left: 10%;
  font-size: 20px;
}
.bm-item-list > * {
  display: flex;
  text-decoration: none;
  padding: 0.7em;
}
.bm-item-list > * > span {
  margin-left: 10px;
  font-weight: 700;
  color: white;
}
</style>
