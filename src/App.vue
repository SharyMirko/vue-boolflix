<template>
  <div id="app">
    <HeaderBoolflix @caunt="caunt = $event" @searchStr="searchRequest($event)" />
    <MainBoolfix :arrMovie="resultsMovie" :caunt="caunt" :arrSeries="resultsSeries" />
  </div>
</template>

<script>
import axios from 'axios'
import HeaderBoolflix from './components/HeaderBoolflix.vue'
import MainBoolfix from './components/MainBoolfix.vue'

export default {
  name: 'App',
  components: {
    HeaderBoolflix,
    MainBoolfix
},
data () {
  return {
    resultsMovie: [],
    resultsSeries: [],
    caunt: 0
  }
},
methods: {
  searchRequest(str){
    axios.get('https://api.themoviedb.org/3/search/movie?api_key=1814a5181699a3f32f15c63dc0665bd9&language=it-IT&query=' + str)
    .then(res => {
      this.resultsMovie = res.data.results
      this.resultsMovie.forEach(item => {
        if (Math.floor(item.vote_average) <= 2) {
          return item.vote_average = 1
        } else {
          item.vote_average = Math.floor(item.vote_average / 2)
        }
      })
    })

    axios.get('https://api.themoviedb.org/3/search/tv?api_key=1814a5181699a3f32f15c63dc0665bd9&language=it-IT&query=' + str).then(resp => {
      this.resultsSeries = resp.data.results
      this.resultsSeries.forEach(item => {
        if (Math.floor(item.vote_average) <= 2) {
          return item.vote_average = 1
        } else {
          item.vote_average = Math.floor(item.vote_average / 2)
        }
      })
    })
  }
}
}
</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body {
  background-color: #141414;
  color: #fff;
}
#app {

}
</style>
