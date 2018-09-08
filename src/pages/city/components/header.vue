<template>
  <div class="header">
    <router-link to="/">
    <span class="iconfont icon-fanhui left"></span>
    </router-link>
    城市选择
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles'

.header
  background-color $bgcolor
  height $headerheight
  line-height $headerheight
  color #ffffff
  text-align center
  .left
    float left
    width 0.64rem
    color #fff
</style>
