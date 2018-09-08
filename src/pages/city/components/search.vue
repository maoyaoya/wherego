<template>
<div>
   <div class="search">
     <input  v-model="keyword" class="input" placeholder="请输入城市名或拼音">
   </div>
   <div class="result" ref="res" v-show="keyword">
      <ul>
        <li 
        class="search-result border-bottom" 
        v-for="(item,index) in list" 
        :key="index"
        @click="handleCityClick(item.name)"
        >
          {{item.name}}
        </li>
        <li class="search-result border-bottom" v-show="hasNodata">没有找到符合的选项</li>
      </ul>
   </div>
</div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapMutations } from 'vuex'
export default {
  name: 'CitySearch',
  props: {
    cities: Object,
  },
  data() {
    return {
      keyword: '',
      timer: null,
      list: []
    }
  },
  watch: {
    keyword() {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        return this.list = []
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 ||
              value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      })
    }
  },
  methods: {
    handleCityClick(city) {
      this.changeCity(city);
      this.$router.push('/');
    },
    ...mapMutations(['changeCity'])
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.res, { mouseWheel: true, click: true });
  },
  computed: {
    hasNodata() {
      return !this.list.length;
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl'

.border-bottom
  &:before
    border-color #ccc
.search
  height 0.72rem
  background $bgcolor
  padding 0 0.1rem
  .input
    height 0.62rem
    line-height 0.62rem
    width 100%
    padding 0 0.1rem
    box-sizing border-box
    border-radius 0.1rem
    text-align center
.result
  z-index 1
  position absolute
  top 1.58rem
  left 0
  right 0
  bottom 0
  overflow hidden
  background-color #ccc
  .search-result
    height 0.64rem
    line-height 0.64rem
    background-color #fff
    padding-left 0.2rem
</style>
