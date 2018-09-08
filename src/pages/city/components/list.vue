<template>
  <div class="list"  ref="wrapper">
    <div>
      <div class="area">
        <div class="title border-topbottom">当前城市</div>
        <div class="button-list">
          <div class="button">
            <div class="button-text">
              {{this.city}}
            </div>
          </div>
        </div>
      </div>
      <div class="area">
        <div class="title border-topbottom">热门城市</div>
        <div class="button-list">
          <div class="button" 
            v-for="item in hot" 
            :key="item.id"
            @click="handleCityClick(item.name)"
            >
            <div class="button-text" >
              {{item.name}}
            </div>
          </div>
        </div>
      </div>
      <div class="area" v-for="(item,key) in cities" :key="key" :ref="key">
        <div class="title border-topbottom">{{key}}</div>
        <div class="item-list border-bottom" 
        v-for='letter in item' 
        :key='letter.id'
        @click="handleCityClick(letter.name)"
        >
          <div class="letter">{{letter.name}}</div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Bscroll from 'better-scroll'
import { mapState, mapMutations } from 'vuex'
export default {
  name: 'CityList',
  props: {
    hot: Array,
    cities: Object,
    letter: String
  },
  methods: {
    handleCityClick(city) {
      this.changeCity(city);
      this.$router.push('/');
    },
    ...mapMutations(['changeCity'])
  },
  computed: {
    ...mapState(['city'])
  },
  mounted() {
    this.scroll = new Bscroll(this.$refs.wrapper, { click: true, mouseWheel: true });
  },
  watch: {
    letter() {
      const element = this.$refs[this.letter][0];
      this.scroll.scrollToElement(element);
    }
  }
}
</script>

<style lang="stylus" scoped>
.border-topbottom
  &:before
    border-color #ccc
  &:after
    border-color #ccc
.border-bottom
  &:before
    border-color #ccc
.list
  position absolute
  left 0
  right 0
  top 1.58rem
  bottom 0
  overflow hidden
  .title
    height 0.54rem
    line-height 0.54rem
    background-color #eee
    padding-left 0.2rem
    color #666
  .button-list
    overflow hidden
    padding 0.1rem 0.6rem 0.1rem 0.1rem
    .button
      float left
      width 33%
      .button-text
        text-align center
        border 0.02rem solid #cccccc
        border-radius 0.06rem
        padding 0.1rem 0
        margin 0.1rem
  .item-list
    .letter
      height 0.76rem
      line-height 0.76rem
      color #666666
      padding-left 0.2rem
</style>
