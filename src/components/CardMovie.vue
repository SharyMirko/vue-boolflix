<template>
  <div @mouseenter="getActor()" class="card-container">
    <div class="img">
      <img
        :src="
          item.poster_path != null
            ? img + item.poster_path
            : 'https://picsum.photos/490'
        "
        alt=""
      />
    </div>
    <div class="content">
      <p>Titolo:</p>
      <span v-if="item.title != item.original_title">{{ item.title }}</span>
      <p>Titolo originale:</p>
      <span>{{ item.original_title }}</span>
      <p>
        Lingua: <lang-flag :iso="item.original_language" :squared="false" />
      </p>
      <p>
        Vote:
        <span v-for="star in item.vote_average" :key="star"
          ><img src="../../public/star-fill.svg" alt=""
        /></span>
        <span v-for="starEmpty in 5 - item.vote_average" :key="starEmpty"
          ><img src="../../public/star.svg" alt=""
        /></span>
      </p>
      <p>Trama:</p>
      <span v-if="item.overview != ''"
        >{{ item.overview.substr(0, 150) }}...</span
      >
      <p>Attori:</p>
      <span v-if="dati != null">{{ dati[0].name + ", " + dati[1].name }}</span>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import LangFlag from "vue-lang-code-flags";
export default {
  name: "CardMovie.vue",
  data() {
    return {
      img: "https://image.tmdb.org/t/p/w342/",
      dati: null,
    };
  },
  props: {
    item: Object,
  },
  components: {
    LangFlag,
  },
  methods: {
    //https://api.themoviedb.org/3/movie/10206/credits?api_key=1814a5181699a3f32f15c63dc0665bd9&language=en-US
    getActor() {
      axios
        .get(
          "https://api.themoviedb.org/3/movie/" +
            this.item.id +
            "/credits?api_key=1814a5181699a3f32f15c63dc0665bd9&language=it-IT"
        )
        .then((res) => {
          this.dati = res.data.cast;
        });
    },
  },
};
</script>

<style scoped lang="scss">
.card-container {
  width: calc((100% - 8rem) / 4);
  margin: 1rem;
  position: relative;
}

.img {
  width: 100%;
  img {
    width: 100%;
    height: 100%;
    object-fit: contain;
  }
}
.content {
  position: absolute;
  top: 0;
  margin: 0;
  background-color: rgb(58, 58, 58);
  width: 100%;
  height: 100%;
  display: none;
}
.card-container:hover .content {
  display: block;
}
</style>
