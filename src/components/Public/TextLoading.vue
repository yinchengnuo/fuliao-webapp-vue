<template>
  <a @click="toAbout" class="text-loading">
    加载中...
  </a>
</template>

<script>
export default {
  name: 'text-loading',
  props: ['name'],
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
.text-loading {
  display: block;
  .wrapper(@position: relative; @height: @header-height; @top: auto; @bottom: 0;);
  line-height: @header-height;
  text-align: center;
}
</style>
