<template>
    <div>
      <form @submit.prevent="registerUser">
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" required>
        
        <label for="login">Login:</label>
        <input type="text" id="login" v-model="login" required>
        
        <label for="name">Name:</label>
        <input type="text" id="name" v-model="name" required>
        
        <label for="birthday">Birthday:</label>
        <input type="date" id="birthday" v-model="birthday" required>
        
        <button type="submit">Register</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from 'axios';
  
  export default {
    data() {
      return {
        email: '',
        login: '',
        name: '',
        birthday: ''
      }
    },
    methods: {
      registerUser() {
        axios.post('http://localhost:8080/users', {
          email: this.email,
          login: this.login,
          name: this.name,
          birthday: this.birthday
        })
        .then(response => {
          console.log(response.data);
          // Действия после успешной регистрации
        })
        .catch(error => {
          console.log(error);
          // Действия при ошибке регистрации
        })
      }
    }
  }
  </script>
  