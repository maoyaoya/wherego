<template>
  <div class="header">
    <div class="left">
      <div class="iconfont icon-fanhui icon"></div>
    </div>
    <div class="middle">
      <div class="iconfont icon-sousuo sousuo"></div>
      <input class="input" type="text" placeholder="请输入城市/景点/游玩主题">
    </div>
    <router-link to="/city">
    <div class="right">
      {{this.city}}
      <span class="iconfont icon-jiantou down-icon"></span>
    </div>
    </router-link>
  </div>
</template>  

<script>
import { mapState } from 'vuex'
export default {
  name: 'HomeHeader',
  computed: {
    ...mapState(['city'])
  },
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles'

.header
  background-color $bgcolor
  height $headerheight
  line-height $headerheight
  color #fff
  display flex
  .left
    float left
    width 0.64rem
    height 0.86rem
    .icon
      text-align center
  .middle
    position relative
    flex 1
    text-align center
    background #fff
    color #ccd6e3
    height 0.64rem
    line-height 0.64rem
    margin-top 0.11rem
    border-radius 0.2rem
    margin-left 0.1rem
    .input
      position absolute
      right 0
      width 92%
      height 0.64rem
      border-radius 0.2rem
      font-size 0.26rem
    .sousuo
      position absolute
      left 0.16rem
      font-size 0.28rem
      top 50%
      transform translateY(-50%)
  .right
    min-width 1.04rem
    height 0.86rem
    float right
    padding 0 0.1rem
    text-align center
    color #fff
    .down-icon
      font-size 0.2rem
</style>