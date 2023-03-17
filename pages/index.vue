<template>
  <div>
    <h1>Welcome to My Todo App</h1>
    <p>This app allows you to create and manage your Todo list.</p>
    <p>To get started, please login using your username and password.</p>
    <router-link to="/login" class="btn btn-primary">Login</router-link>
  </div>
</template>

<script>
export default {
  name: 'HomePage',
}
</script>
