<template>
<div class="card-container"><div class="img"><img :src="img + item.poster_path" alt=""></div>
<div class="content">{{item.title}}<br>{{item.original_title}}<br><lang-flag :iso="item.original_language" :squared="false" /><br>{{item.vote_average}}</div>
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
    img {
        width: 100%;
        height: 100%;
        object-fit: contain;
    }
}

.img {
    width: 100%;
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