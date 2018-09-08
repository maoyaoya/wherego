<template>
 <div>
   <div class="title">周末去哪</div>
   <div class="week" v-for="item in week" :key="item.id">
    <div class="img">
     <img class="week-img" :src="item.imgUrl">
    </div>
    <div class="text">
     <p class="week-title">{{item.title}}</p>
     <p class="week-desc">{{item.desc}}</p>
    </div>
   </div>
</div>
</template>

<script>
export default {
  name: 'HomeWeek',
  props: {
    week: Array
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/mixin.styl'

.title
  height 0.8rem
  line-height 0.8rem
  background-color #eee
  padding-left 0.44rem
.week
  .img
    overflow hidden
    height 0
    padding-bottom 38%
    .week-img
      width 100%
  .text
    padding 0.1rem
    .week-title
      height 0.54rem
      line-height 0.54rem
      font-size 0.34rem
      color #000
      ellipsis()
    .week-desc
      line-height 0.4rem
      color #ccc
      ellipsis()
</style>