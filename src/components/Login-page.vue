<template>
    <div class="login-container">
      <form @submit.prevent="handleLogin">
        <h2>Login</h2>
        <div class="login-page">
          <label for="username">Username</label>
          <input type="text" v-model="username" id="username" required />
        </div>
        <div class="login-page">
          <label for="password">Password</label>
          <input type="password" v-model="password" id="password" required />
        </div>
        <button type="submit">Login</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        username: '',
        password: ''
      }
    },
    methods: {
      async handleLogin() {
        const credentials = {
          username: this.username,
          password: this.password
        };
        // Mock authentication request
        try {
          const response = await this.authenticate(credentials);
          if (response.success) {
            alert('Login successful!');
          } else {
            alert('Invalid username or password.');
          }
        } catch (error) {
          alert('An error occurred during login.');
        }
      },
      authenticate(credentials) {
        // Mock API call
        return new Promise((resolve) => {
          setTimeout(() => {
            if (credentials.username === 'user' && credentials.password === 'password') {
              resolve({ success: true });
            } else {
              resolve({ success: false });
            }
          }, 1000);
        });
      }
    }
  }
  </script>
  
  <style scoped>
  .login-container {
    max-width: 400px;
    margin: 50px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 4px;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
  }
  
  h2 {
    text-align: center;
    margin-bottom: 20px;
  }
  
  .form-group {
    margin-bottom: 15px;
  }
  
  label {
    display: block;
    margin-bottom: 5px;
    margin-top: 5px;
  }
  
  input {
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
  }
  
  button {
    width: 100%;
    padding: 10px;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin-top: 10px;
  }
  
  button:hover {
    background-color: #0056b3;
  }
  </style>
  