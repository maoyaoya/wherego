<template>
<div>
  <detail-header></detail-header>
  <detail-banner :bannerimg="bannerImg" :sightName="sightName" :gallaryImgs="gallaryImgs"></detail-banner>
  <div class="content">
    <detail-list :list="categoryList"></detail-list>
  </div>
</div>
</template>

<script>
import axios from 'axios'
import DetailHeader from './components/header'
import DetailBanner from './components/banner'
import DetailList from './components/list'
export default {
  name: 'detail',
  components: {
    DetailHeader,
    DetailBanner,
    DetailList,
  },
  data() {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      categoryList: []
    }
  },
  methods: {
    getDetail() {
      axios.get('/api/detail.json').then(this.getDetailSucc)
    },
    getDetailSucc(res) {
      res = res.data;
      if (res.ret && res.data) {
        const data = res.data;
        this.sightName = data.sightName;
        this.bannerImg = data.bannerImg;
        this.gallaryImgs = data.gallaryImgs;
        this.categoryList = data.categoryList;
      }
    }
  },
  mounted() {
    this.getDetail();
  }
}
</script>

<style lang="stylus" scoped>
.content
  height 50rem
</style>
