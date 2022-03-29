<template>
<div class="card-container"><div class="img"><img :src="img + item.poster_path" alt=""></div>
<div class="content"><p>Titolo:</p> <span>{{item.name}}</span> <p>Titolo originale: </p> <span>{{item.original_name}}</span><p>Lingua: <lang-flag :iso="item.original_language" :squared="false" /></p>
<p>Vote: <span v-for="star in item.vote_average" :key="star"><img src="../../public/star-fill.svg" alt=""></span> <span v-for="starEmpty in 5 - item.vote_average" :key="starEmpty"><img src="../../public/star.svg" alt=""></span> </p>
<p>Trama:</p> <span v-if="item.overview != ''">{{ item.overview.substr(0, 150) }}...</span>
</div>
</div>  
</template>

<script>
import LangFlag from 'vue-lang-code-flags';
export default {
name: 'CardMovie.vue',
data () {
    return {
        img: 'https://image.tmdb.org/t/p/w342/',
    }
},
props: {
   item: Object 
},
components: {
    LangFlag
}
}
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