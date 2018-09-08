<template>
<div ref="wrapper">
  <div>
    <router-link to="/">
    <div class="circle iconfont icon-fanhui" v-show="showAbs"></div>
    </router-link>
    <div  class="header-fixed" v-show="!showAbs" :style="opacityStyle">
      <router-link to="/">
      <span class="iconfont icon-fanhui left"></span>
      </router-link>
      景点详情
    </div>
  </div>
</div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data() {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleSceoll() {
      const top = document.documentElement.scrollTop;
      if (top > 60) {
        this.showAbs = false;
        let opacity = top / 140;
        opacity = opacity > 1 ? 1 : opacity;
        return this.opacityStyle = { opacity };
      } else {
        this.showAbs = true;
      }
    }
  },
  activated() {
    window.addEventListener('scroll', this.handleSceoll);
  },
  deactivated() {
    window.addEventListener('scroll', this.handleSceoll);
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles'

.circle
  width 0.8rem
  height 0.8rem
  line-height 0.8rem
  background rgba(0, 0, 0, 0.3)
  border-radius 50%
  text-align center
  color #fff
  position absolute
  top 0.2rem
  left 0.2rem
  z-index 2
.header-fixed
  position fixed
  top 0
  right 0
  left 0
  background-color $bgcolor
  height $headerheight
  line-height $headerheight
  color #ffffff
  text-align center
  font-size 0.32rem
  z-index 2
  .left
    float left
    width 0.64rem
    color #fff
</style>

