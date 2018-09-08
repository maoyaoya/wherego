<template>
   <div class="gallary" @click="handleClickClose">
    <div class="content">
     <swiper :options="swiperOption">
       <swiper-slide v-for="(item ,index) in gallaryImgs" :key="index">
         <img class="swiper-img" :src="item" />
       </swiper-slide>
       <div class="swiper-pagination"  slot="pagination"></div>
     </swiper>
    </div>
   </div>
</template>

<script>
export default {
  name: 'CommonGallary',
  props: {
    gallaryImgs: Array
  },
  data() {
    return {
      swiperOption: {
        pagination: {
          el: '.swiper-pagination',
          type: 'fraction'
        },
        observeParents: true,
        observer: true
      }
    }
  },
  methods: {
    handleClickClose() {
      this.$emit('close');
    }
  }
}
</script>

<style lang="stylus" scoped>
.content>>>.swiper-container
  overflow inherit
.gallary
  display flex
  flex-direction column
  justify-content center
  position fixed
  top 0
  left 0
  right 0
  bottom 0
  background-color #000
  z-index 99
  .content
    width 100%
    height 0
    padding-bottom 100%
    .swiper-img
      width 100%
      height 8.28rem
    .swiper-pagination
      color #fff
      bottom -1rem
</style>
