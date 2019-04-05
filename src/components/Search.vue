<template>
  <div class="searchWrapper">
    <input type="text" name="search" id="search" placeholder="search..." @input="handleInput">
  </div>
</template>
<script>
export default {
  name: "Search",
  methods: {
    handleInput(e) {
      this.$emit("input", e.target.value);
    }
  }
};
</script>
<style lang="scss" scoped>
input {
  width: 300px;
  padding: 10px;
  border: none;
  border-bottom: 2px solid #42b983;
  background: transparent;
  font-size: 12px;
  transition: 0.2s ease-in;
  &:focus {
    outline: none;
    background: #42b983;
    color: #fff;
  }
}
</style>
