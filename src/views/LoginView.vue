<template>
  <div class="login-container">
    <h2>Login</h2>
    <form @submit.prevent="login">
      <div class="form-group">
        <label for="username">Username:</label>
        <input type="text" id="username" v-model="username" placeholder="Username" required />
      </div>
      <div class="form-group">
        <label for="password">Password:</label>
        <input type="password" id="password" v-model="password" placeholder="Password" required />
      </div>
      <button type="submit">Login</button>
    </form>
    <p v-if="loginError" class="error-message">{{ loginError }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      username: '',
      password: '',
      loginError: ''
    }
  },
  methods: {
    login() {
      if (this.username === 'admin' && this.password === 'password') {
        // Successful Login
        console.log('Login successful')
        this.loginError = ''
        // Redirecting to Dashboard
        this.$router.push('/dashboard')
      } else {
        // Display failed attemp
        this.loginError = 'Invalid username or password'
      }
    }
  }
}
</script>

<style lang="scss" scoped>
$primary-color: #24408e;
.login-container {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid $primary-color;
  border-radius: 5px;
}

.form-group {
  margin-bottom: 15px;
}

input[type='text'],
input[type='password'] {
  width: 100%;
  padding: 10px;
  border: 1px solid $primary-color;
  border-radius: 5px;
}

button {
  padding: 10px 20px;
  background-color: $primary-color;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

.error-message {
  color: red;
}
</style>
