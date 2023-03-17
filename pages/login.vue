<template>
    <div>
      <h1>Login</h1>
      <form>
        <div class="form-group">
          <label for="username">Username</label>
          <input v-model="username" type="text" class="form-control" id="username" name="username">
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input v-model="password" type="password" class="form-control" id="password" name="password">
        </div>
        <button type="submit" class="btn btn-primary" @click.prevent="login()">Login</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    name: 'LoginPage',
    data() {
      return {
        username: '',
        password: ''
      }
    },
    methods: {
      login() {
        if (this.username === 'user1' && this.password === 'password1') {
          this.$store.commit('login', 'user1')
          this.$router.push('/todos')
        } else if (this.username === 'user2' && this.password === 'password2') {
          this.$store.commit('login', 'user2')
          this.$router.push('/todos')
        } else if (this.username === 'user3' && this.password === 'password3') {
          this.$store.commit('login', 'user3')
          this.$router.push('/todos')
        } else {
          alert('Invalid username or password')
        }
      }
    }
  }
  </script>
  