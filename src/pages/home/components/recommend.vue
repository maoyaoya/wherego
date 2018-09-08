<template>
 <div>
  <div class="title">热销推荐</div>
  <router-link tag="div" :to="'/detail/'+list.id" class="item" v-for="list in recommend" :key="list.id">
    <img class="item-img" :src="list.imgUrl">
    <div class="item-text">
      <p class="item-title">{{list.title}}</p>
      <p class="item-desc">{{list.desc}}</p>
      <button class="item-button">查看详情</button>
    </div>
  </router-link>
</div>
</template>

<script>
export default {
  name: 'HomeRecommend',
  props: {
    recommend: Array
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
.item
  height 1.9rem
  overflow hidden
  display flex
  border-bottom 1px solid #ccc
  .item-img
    width 1.7rem
    height 1.7rem
    padding 0.1rem
  .item-text
    flex 1
    padding 0.1rem
    .item-title
      line-height 0.54rem
      height 0.54rem
      font-size 0.34rem
      color #000
      ellipsis()
    .item-desc
      line-height 0.4rem
      color #ccc
      ellipsis()
    .item-button
      background-color #ff9300
      color #ffffff
      margin-top 0.2rem
      padding 0 0.1rem
</style>