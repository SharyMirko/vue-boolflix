<template>
  <div class="main-header">
    <div class="logo"><h1>Boolflix</h1></div>
    <input
      type="text"
      @keyup="
        $emit('searchStr', searchStr);
        caunt++;
        $emit('caunt', caunt);
      "
      v-model="searchStr"
      placeholder="cerca "
      name="search"
      id="search"
    />
  </div>
</template>

<script>
export default {
  name: "HeaderBoolflix",
  data() {
    return {
      searchStr: null,
      caunt: 0,
    };
  },
};
</script>

<style lang="scss" scoped>
.main-header {
  height: 4rem;
  background-color: #232323;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
#search {
  height: 2rem;
  margin-right: 1rem;
}

.logo {
  margin-left: 1rem;
  h1 {
    color: #e50914;
  }
}
</style>
