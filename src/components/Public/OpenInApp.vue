<template>
  <a @click="toAbout" class="open-in-app">
    APP内打开
  </a>
</template>

<script>
export default {
  name: 'OpenIApp',
  methods: {
    toAbout () {
      this.$router.push({
        name: 'About'
      })
    }
  }
}
</script>

<style lang="less" scoped>
.open-in-app {
  .wrapper(@position: fixed; @width: calc(@header-height * 3); @left:50%; @height: @header-height; @top: auto; @bottom: 10vh;);
  z-index: 2;
  color: #fff;
  border-radius: @header-height;
  margin-left: calc(-@header-height * 1.5);
  text-align: center;
  line-height: @header-height;
  background: rgb(0, 225, 255);
}
</style>
