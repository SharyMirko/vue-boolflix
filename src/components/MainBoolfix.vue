<template>
  <div class="main-container">
    <h1 v-if="arrMovie.length != 0">Movies</h1>
    <CardMovie v-for="item in arrMovie" :key="item.id" :item="item" />
    <h1 v-if="arrMovie.length != 0">Series</h1>
    <CardSeries v-for="item in arrSeries" :key="item.id" :item="item" />
    <h1 v-if="arrMovie.length == 0 && caunt > 0">
      Non trovo nulla nei film o serie :(
    </h1>
  </div>
</template>

<script>
import CardMovie from "./CardMovie.vue";
import CardSeries from "./CardSeries.vue";
export default {
  name: "MainBoolflix",
  props: {
    arrMovie: Array,
    arrSeries: Array,
    caunt: Number,
  },
  components: {
    CardMovie,
    CardSeries,
  },
};
</script>

<style scoped lang="scss">
.main-container {
  width: 90vw;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  h1 {
    display: block;
    width: 100%;
  }
}
</style>
