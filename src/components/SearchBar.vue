<template>
    <div class="search-bar">
      <input
        type="text"
        placeholder="Поиск фильма..."
        v-model="query"
        @input="searchFilms"
      />
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        query: "",
      };
    },
    methods: {
      searchFilms() {
        this.$emit("search", this.query);
      },
    },
  };
  </script>
  
  <style>
  .search-bar {
    margin-bottom: 20px;
  }
  </style>
  