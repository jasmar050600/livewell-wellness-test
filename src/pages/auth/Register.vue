<template>
  <div class="auth-container">
    <h2 class="auth-title">Register</h2>
    <p class="auth-subtitle">
      Take your first step toward a healthier future.
    </p>
    <form @submit.prevent="registerUser" class="auth-form">
      <div class="form-group">
        <label for="username">Username:</label>
        <input type="text" id="username" v-model="username" required>
      </div>
      <div class="form-group">
        <label for="email">Email:</label>
        <input type="email" id="email" v-model="email" required>
      </div>
      <div class="form-group">
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" required>
      </div>
      <div class="form-group">
        <label for="phoneRegion">Cellular Region:</label>
        <select id="phoneRegion" v-model="phoneRegion" required>
          <option value="+63">Philippines (+63)</option>
          <option value="+1">United States (+1)</option>
          <option value="+44">United Kingdom (+44)</option>
          <option value="+34">Spain (+34)</option>
          <option value="+33">France (+33)</option>
          <option value="+49">Germany (+49)</option>
          <option value="+39">Italy (+39)</option>
          <option value="+351">Portugal (+351)</option>
          <option value="+7">Russia (+7)</option>
          <option value="+86">China (+86)</option>
          <option value="+81">Japan (+81)</option>
          <option value="+82">South Korea (+82)</option>
          <!-- Add more options as needed -->
        </select>
      </div>
      <div class="form-group phone-otp-group">
  <label for="phoneNumber">Phone Number:</label>
  <div class="phone-otp-wrapper">
    <input type="tel" id="phoneNumber" v-model="phoneNumber" required>
    <button type="button" @click="sendOTP" class="send-otp-button">SEND OTP</button>
  </div>
</div>

      <div class="form-group">
        <label for="language">Preferred Language:</label>
        <select id="language" v-model="language" required>
          <option value="en">English</option>
          <option value="es">Español</option>
          <option value="fr">Français</option>
          <option value="de">Deutsch</option>
          <option value="it">Italiano</option>
          <option value="pt">Português</option>
          <option value="ru">Русский</option>
          <option value="zh">中文</option>
          <option value="ja">日本語</option>
          <option value="ko">한국어</option>
        </select>
      </div>
      <div class="form-group">
        <label for="sponsor">Sponsor (Optional):</label>
        <input type="text" id="sponsor" v-model="sponsor" placeholder="Enter sponsor's username or referral code">
      </div>
      <button type="submit" class="auth-button">Register</button>
    </form>
    <p class="auth-link">
      Already have an account? <router-link to="/auth/login">Login here</router-link>
    </p>
  </div>
</template>

<script>
export default {
  name: 'Register',
  data() {
    return {
      username: '',
      email: '',
      password: '',
      phoneRegion: '+63',
      phoneNumber: '',
      language: 'en',
      sponsor: ''
    }
  },
  methods: {
    registerUser() {
      // Implement registration logic here
      console.log('Registering user:', {
        username: this.username,
        email: this.email,
        phoneNumber: `${this.phoneRegion}${this.phoneNumber}`,
        language: this.language,
        sponsor: this.sponsor
      });
      // You would typically make an API call here
      // Include the sponsor information in the registration process
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
  margin-bottom: 1rem;
  font-family: 'Times New Roman', Times, serif;
  font-weight: 300;
}

.auth-subtitle {
  text-align: center;
  color: #4a0e4e;
  font-size: 1rem;
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

input, select {
  width: 100%;
  padding: 0.75rem;
  border: 1px solid #e0e0e0;
  border-radius: 4px;
  font-size: 1rem;
  color: #2c3e50;
  background-color: #f5f5f5;
}

input::placeholder {
  color: #999999;
}

input:focus, select:focus {
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
  margin-top: 1rem;
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

.phone-otp-group {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  margin-bottom: 15px; /* Adjust the space between the form-group and next element */
}

.phone-otp-wrapper {
  display: flex;
  align-items: center; /* This aligns the button with the input field */
}

#phoneNumber {
  width: calc(100% - 120px); /* Adjust the width of the phone number input to make space for the button */
  padding: 5px;
  margin-right: 10px;
}

.send-otp-button {
  padding: 5px 10px;
  background-color: #5a2a7b; /* Match theme color */
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.send-otp-button:hover {
  background-color: #70348c;
}


</style>