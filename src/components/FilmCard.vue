<template>
    <div class="film-card">
      <h2>{{ film.name }}</h2>
      <p>{{ film.description }}</p>
      <p>Дата выхода: {{ film.releaseDate }}</p>
      <p>Длительность: {{ film.duration }} минут</p>
      <p>Средний рейтинг: {{ film.averageScore }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      film: {
        type: Object,
        required: true,
      },
    },
  };
  </script>
  
  <style>
  .film-card {
    border: 1px solid #ccc;
    padding: 10px;
    margin-bottom: 10px;
  }
  
  .film-card:hover {
  transform: scale(1.05) rotate(3deg);
  box-shadow: 0 8px 16px rgba(0, 0, 0, 0.3);
  transition: all 0.3s ease-in-out;
}

  </style>
  