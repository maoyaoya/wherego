<template>
 <div class="swiper">
   <swiper :options="swiperOption">
    <!-- slides -->
    <swiper-slide v-for="item in list" :key="item.id">
      <img class="swiper-img" :src="item.imgUrl"></swiper-slide>
    <!-- Optional controls -->
    <div class="swiper-pagination"  slot="pagination"></div>
  </swiper>
 </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  props: {
    list: Array
  },
  data() {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination'
        },
        loop: true,
      }
    }
  }
}
</script>

<style lang="stylus" scoped>
.swiper>>>.swiper-pagination-bullet-active
  background-color #fff
.swiper
  overflow hidden
  width 100%
  height 0
  padding-bottom 31.25%
  .swiper-img
    width 100%
    height 2.6rem
</style>