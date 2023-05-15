<template>
    <div class="film-list">
      <SearchBar @search="searchFilms" />
      <div v-if="loading" class="loading-message">Загрузка...</div>
      <div v-else-if="error" class="error-message">{{ error }}</div>
      <div v-else-if="films.length === 0" class="empty-message">Нет фильмов</div>
      <div v-else>
        <FilmCard v-for="film in filteredFilms" :key="film.id" :film="film" />
      </div>
    </div>
  </template>
  
  <script>
  import FilmCard from "@/components/FilmCard.vue";
  import SearchBar from "@/components/SearchBar.vue";
  
  export default {
    data() {
      return {
        films: [],
        loading: false,
        error: null,
        query: "",
      };
    },
    components: {
      FilmCard,
      SearchBar,
    },
    created() {
      this.fetchFilms();
    },
    methods: {
      fetchFilms() {
        this.loading = true;
        fetch("http://localhost:8080/films")
          .then((response) => response.json())
          .then((data) => {
            this.films = data;
            this.loading = false;
          })
          .catch((error) => {
            this.error = error.message;
            this.loading = false;
          });
      },
      searchFilms(query) {
        this.query = query;
      },
    },
    computed: {
      filteredFilms() {
        if (this.query) {
          return this.films.filter((film) =>
            film.name.toLowerCase().includes(this.query.toLowerCase())
          );
        } else {
          return this.films;
        }
      },
    },
  };
  </script>
  
  <style>
  .film-list {
    margin-bottom: 20px;
  }
  
  .loading-message,
  .error-message,
  .empty-message {
    margin: 10px 0;
    padding: 10px
  }
  
  .loading-message {
  color: #999;
}

.error-message {
  color: #f00;
}

.empty-message {
  color: #999;
}
</style>
