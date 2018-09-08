<template>
<div>
  <div class="banner" @click="handleClick">
    <img class="banner-img" :src=" bannerimg" />
    <div class="banner-text">
      <div class="banner-title">{{this.sightName}}</div>
      <div class="banner-number"><span class="iconfont icon-size">&#xe692; </span>
       {{this.gallaryImgs.length}}
      </div>
    </div>
  </div>
  <fade-animate>
  <common-gallary
  :gallaryImgs="gallaryImgs"
  @close="handleClose"
  v-show="show"
  ></common-gallary>
  </fade-animate>
</div>
</template>

<script>
import CommonGallary from '../../../common/gallary/gallary'
import FadeAnimate from '../../../common/fade/animate'
export default {
  name: 'DetailBanner',
  components: {
    CommonGallary,
    FadeAnimate,
  },
  props: {
    bannerimg: String,
    sightName: String,
    gallaryImgs: Array
  },
  data() {
    return {
      show: false
    }
  },
  methods: {
    handleClose() {
      this.show = false;
    },
    handleClick() {
      this.show = true;
    }
  }
}
</script>

<style lang="stylus" scoped>
.banner
  position relative
  overflow hidden
  height 0
  padding-bottom 55%
  .banner-img
    width 100%
  .banner-text
    position absolute
    left 0
    right 0
    bottom 0
    line-height 0.6rem
    color #fff
    display flex
    background-image linear-gradient(
      top,
      rgba(0, 0, 0, 0),
      rgba(0, 0, 0, 0.8)
    )
    .banner-title
      flex 1
      font-size 0.32rem
      padding-left 0.2rem
    .banner-number
      line-height 0.32rem
      background rgba(0, 0, 0, 0.8)
      padding 0 0.4rem
      border-radius 0.2rem
      font-size 0.24rem
      margin-top 0.15rem
      .icon-size
        font-size 0.24rem
</style>
