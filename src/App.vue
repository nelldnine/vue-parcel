<template>
  <div>
    <h1>App</h1>
    <router-view></router-view>
  </div>
</template>

<script>
import VueRouter from 'vue-router';
import Users from './pages/Users';
import User from './pages/User';

const router = new VueRouter({
  routes: [
    { path: '/user/:id', component: User, name: 'user' },
    { path: '/', component: Users }
  ]
});

export default {
  router
}
</script>

<style>
h1 {
  color: red;
}
</style>
