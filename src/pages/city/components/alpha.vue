<template>
    <ul class="alpha">
      <li class="letter" 
      v-for="item in letters" 
      :key="item"
      :ref="item"
      @click="handleClick"
      @touchstart="touchStart"
      @touchmove="touchMove"
      @touchend="touchEnd"
      >{{item}}</li>
    </ul>
</template>

<script>
export default {
  name: 'CityAlpha',
  props: {
    cities: Object
  },
  data() {
    return {
      istouch: false,
      startY: '',
      timer: null
    }
  },
  updated() {
    this.startY = this.$refs['A'][0].offsetTop;
  },
  methods: {
    handleClick(e) {
      this.$emit('change', e.target.innerHTML);
    },
    touchStart() {
      this.istouch = true;
    },
    touchMove(e) {
      if (this.istouch) {
        if (this.timer) {
          clearTimeout(this.timer);
        }
        this.timer = setTimeout(() => {
          const touchY = e.touches[0].clientY - 79;
          const index = Math.floor((touchY - this.startY) / 20);
          if (index >= 0 && index < this.letters.length) {
            this.$emit('change', this.letters[index]);
          }
        }, 16)
      }

    },
    touchEnd() {
      this.istouch = false;
    }
  },
  computed: {
    letters() {
      let letters = [];
      for (var i in this.cities) {
        letters.push(i);
      }
      return letters;
    }
  }
}
</script>

<style lang="stylus" scoped>
@import '~@/assets/styles/varibles.styl'

.alpha
  display flex
  flex-direction column
  justify-content center
  position absolute
  top 1.58rem
  right 0
  bottom 0
  width 0.4rem
  .letter
    line-height 0.4rem
    text-align center
    color $bgcolor
</style>
