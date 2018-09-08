<template>
<div>
  <city-header></city-header>
  <city-search :cities="cities"></city-search>
  <city-list :hot="hotCities" :cities="cities" :letter="letter"></city-list>
  <city-alpha :cities="cities" @change="getLetter"></city-alpha>
</div>
</template>

<script>
import CityHeader from './components/header'
import CityList from './components/list'
import CitySearch from './components/search'
import CityAlpha from './components/alpha'
import axios from 'axios'
export default {
  name: 'city',
  components: {
    CityHeader,
    CityList,
    CitySearch,
    CityAlpha
  },
  data() {
    return {
      hotCities: [],
      cities: {},
      letter: '',
    }
  },
  methods: {
    getCityInfo() {
      axios.get('/api/city.json').then(this.getCityInfoSucc);
    },
    getCityInfoSucc(res) {
      res = res.data;
      if (res.ret && res.data) {
        const data = res.data;
        this.hotCities = data.hotCities;
        this.cities = data.cities;
      }
    },
    getLetter(letter) {
      this.letter = letter;
    }
  },
  mounted() {
    this.getCityInfo();
  }
}
</script>

<style lang="stylus" scoped>
</style>
