<template>
  <div class="auth-container">
    <h2 class="auth-title">Login</h2>
    <form @submit.prevent="loginUser" class="auth-form">
      <div class="form-group">
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" required>
      </div>
      <div class="form-group">
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required>
      </div>
      <button type="submit" class="auth-button">Login</button>
    </form>
    <p class="auth-link">
      Don't have an account? <router-link to="/auth/register">Register here</router-link>
    </p>
  </div>
</template>

<script>
export default {
  name: 'Login',
  data() {
    return {
      email: '',
      password: ''
    }
  },
  methods: {
    loginUser() {
      // Implement login logic here
      console.log('Logging in user:', this.email);
      // You would typically make an API call here
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;600&display=swap');

.auth-container {
  max-width: 400px;
  margin: 2rem auto;
  padding: 2rem;
  background-color: #ffffff;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  font-family: 'Times New Roman', sans-serif;
}

.auth-title {
  text-align: center;
  color: #4a0e4e;
  font-size: 2.5rem;
  margin-bottom: 1.5rem;
  font-family: 'Times New Roman', Times, serif;
  font-weight: 300;
}

.auth-form {
  display: flex;
  flex-direction: column;
}

.form-group {
  margin-bottom: 1rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  color: #2c3e50;
}

input {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
  font-size: 1rem;
  color: #333333; /* Darker text color for better visibility */
  background-color: #f5f5f5; /* Light gray background for subtle contrast */
}

input::placeholder {
  color: #999999; /* Light gray color for placeholders */
}

/* Optional: Add a focus style for better user experience */
input:focus {
  outline: none;
  border-color: #4a0e4e;
  box-shadow: 0 0 0 2px rgba(74, 14, 78, 0.2);
}

.auth-button {
  background-color: #4a0e4e;
  color: white;
  border: none;
  padding: 0.75rem;
  border-radius: 4px;
  font-size: 1rem;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.auth-button:hover {
  background-color: #3a0b3e;
}

.auth-link {
  text-align: center;
  margin-top: 1rem;
  color: #2c3e50;
}

.auth-link a {
  color: #4a0e4e;
  text-decoration: none;
}

.auth-link a:hover {
  text-decoration: underline;
}
</style>