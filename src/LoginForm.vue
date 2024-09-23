<template>
    <div class="container" >
      <div class="form-container">
        <form @submit.prevent="login" class="login-form">
          <h1>Login</h1>
          <input v-model="username" placeholder="Username" autocomplete="off" required>
          <input v-model="password" type="password" placeholder="Password" autocomplete="new-password" required>
          <button class="btn btn-form" type="submit">Login</button>
        </form>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'LoginForm',
    data() {
      return {
        username: '',
        password: '',
      };
    },
    mounted() {
      this.username = '';
      this.password = '';
    },
    methods: {
      login() {
        this.$emit('login', { id: Date.now(), name: this.username });
      }
    }
  };
  </script>
  
  <style>

  .container {
    display: flex;
    justify-content: center;
    align-items: center;
    height: 70vh;
  }
  
  .form-container {
    width: 500px;
    margin: 0 auto;
    padding: 50px;
    background-color: #333;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    color: #fff;
  }
  
  h1 {
    text-align: center;
    margin-bottom: 30px;
    font-size: 36px;
    color: #b38bff;
  }
  
  form {
    display: flex;
    flex-direction: column;
  }
  
  input {
    padding: 12px;
    border: none;
    border-radius: 5px;
    margin-bottom: 20px;
    font-size: 16px;
    color: #fff;
    background-color: #555;
  }
  
  button {
    padding: 10px;
    background-color: #b38bff;
    color: #fff;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    font-size: 18px;
    transition: background-color 0.2s ease-in-out;
  }
  
  button:hover {
    background-color: #8c5fb2;
  }
  
  a {
    text-decoration: none;
    color: #b38bff;
    font-size: 18px;
    transition: color 0.2s ease-in-out;
  }
  
  a:hover {
    color: #8c5fb2;
  }
  
  p {
    text-align: center;
    margin: 8px;
  }
  </style>
  