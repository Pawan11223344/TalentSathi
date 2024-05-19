<template>
  <div class="signup">
    <h1>User Sign Up</h1>
    <form @submit.prevent="signUp">
      <input v-model="name" type="text" placeholder="Name" required />
      <input v-model="email" type="email" placeholder="Email" required />
      <input v-model="password" type="password" placeholder="Password" required />
      <button type="submit">Sign Up</button>
    </form>
  </div>
</template>

<script>
import { useAuthStore } from '../stores/auth';

export default {
  name: 'UserSignUp',
  data() {
    return {
      name: '',
      email: '',
      password: ''
    };
  },
  methods: {
    signUp() {
      const authStore = useAuthStore();
      authStore.signUp(this.name, this.email, this.password);
    }
  }
};
</script>
