<template>
<div class="main-container">
<CardMovie v-for="item in arrMovie" :key="item.id" :item="item" />
</div>  
</template>

<script>
import CardMovie from "./CardMovie.vue";
export default {
    name: "MainBoolflix",
    props: {
        arrMovie: Array,
        arrSeries: Array
    },
    components: { CardMovie }
}
</script>

<style scoped lang="scss">
.main-container {
    width: 90vw;
    margin: 0 auto;
    display: flex;
    flex-wrap: wrap;
}
</style>