<template>
  <div class="app">
    <AppHeader />
    <h1>Список фильмов</h1>
    <FilmList />
  </div>
</template>

<script>
import AppHeader from "@/components/AppHeader.vue";
import FilmList from "@/components/FilmList.vue";

export default {
  name: "App",
  components: {
    AppHeader,
    FilmList,
  },
};
</script>



<style>
.app {
  max-width: 600px;
  margin: 0 auto;
}
</style>
