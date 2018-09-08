<template>
  <div class="content">
    <div class="item" v-for="(item,index) in list"  :key="index">
      <div class="item-list">
      {{item.title}}
      </div>
    <div class="item-next" v-if="item.children">
      <detail-list :list="item.children"></detail-list>
    </div>
</div>  
</div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    list: Array
  }
}
</script>

<style lang="stylus" scoped>
.content
  position relative
  top 0.06rem
  .item
    .item-list
      padding 0 0.2rem
      line-height 0.8rem
      border-bottom 1px solid #eee
      font-size 0.32rem
    .item-next
      padding-left 0.2rem
</style>
