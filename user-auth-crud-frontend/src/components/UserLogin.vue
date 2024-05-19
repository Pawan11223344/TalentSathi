<template>
  <div class="login">
    <h1>User Login</h1>
    <form @submit.prevent="login">
      <input v-model="email" type="email" placeholder="Email" required />
      <input v-model="password" type="password" placeholder="Password" required />
      <button type="submit">Login</button>
    </form>
  </div>
</template>

<script>
import { useAuthStore } from '../stores/auth';

export default {
  name: 'UserLogin',
  data() {
    return {
      email: '',
      password: ''
    };
  },
  methods: {
    login() {
      const authStore = useAuthStore();
      authStore.login(this.email, this.password);
    }
  }
};
</script>
