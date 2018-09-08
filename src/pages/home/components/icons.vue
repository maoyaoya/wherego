<template>
  
<swiper :options="swiperOption" class="bg">
    <!-- slides -->
  <swiper-slide v-for="(page,index) in pages" :key="index">
    <div class="iconlist">
      <div class="icon" v-for="item in page" :key="item.id">
        <div class="icon-img">
          <img class="swiper-img" :src="item.imgUrl">
        </div>
        <p class="icon-text">{{item.desc}}</p>
    </div>
  </div>  
  </swiper-slide >
  <!-- Optional controls -->
  <div class="swiper-pagination"  slot="pagination"></div>
</swiper>
  
</template>

<script>
export default {
  name: 'HomeIcon',
  props: {
    icon: Array
  },
  data() {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination'
        }
      }
    }
  },
  computed: {
    pages() {
      const pages = [];
      this.icon.forEach((item, index) => {
        const page = Math.floor(index / 8);
        if (!pages[page]) {
          pages[page] = [];
        };
        pages[page].push(item);
      })
      return pages;
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/mixin.styl'

.bg>>>.swiper-pagination-bullets
  bottom 0.1rem
.iconlist
  overflow hidden
  width 100%
  height 0
  padding-bottom 50%
  .icon
    box-sizing border-box
    float left
    width 25%
    height 0
    overflow hidden
    padding-bottom 25%
    position relative
    .icon-img
      position absolute
      top 0
      left 0
      right 0
      bottom 0.54rem
      padding 0.2rem
      .swiper-img
        height 100%
        display block
        margin 0 auto
    .icon-text
      position absolute
      left 0
      right 0
      bottom 0.26rem
      text-align center
      height 0.44rem
      line-height 0.44rem
      ellipsis()
</style>