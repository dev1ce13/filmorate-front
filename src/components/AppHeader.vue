<template>
    <header class="header">
      <div class="header-logo">
        <img src="../assets/logo.png" alt="Logo" />
      </div>
      <nav class="header-nav">
        <ul>
          <li><router-link to="/">Главная</router-link></li>
          <li><router-link to="/films">Фильмы</router-link></li>
          <li><router-link to="/about">О нас</router-link></li>
          <li v-if="isAuthenticated"><router-link to="/profile">Профиль</router-link></li>
          <li v-if="!isAuthenticated"><router-link to="/login">Войти</router-link></li>
          <li v-if="!isAuthenticated"><router-link to="/registration">Зарегистрироваться</router-link></li>
          <li v-if="isAuthenticated" @click="logout">Выйти</li>
        </ul>
      </nav>
    </header>
  </template>
  
  <script>
  export default {
    name: 'AppHeader',
    computed: {
      isAuthenticated() {
        // здесь проверка на авторизацию пользователя
        return false;
      }
    },
    methods: {
      logout() {
        // здесь логика выхода из аккаунта
      }
    }
  }
  </script>
  
  <style scoped>
  .header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
  }
  
  .header-logo img {
    height: 50px;
  }
  
  .header-nav ul {
    display: flex;
    list-style: none;
    margin: 0;
    padding: 0;
  }
  
  .header-nav ul li {
    margin-right: 20px;
  }
  
  .header-nav ul li:last-child {
    margin-right: 0;
  }
  </style>
  
