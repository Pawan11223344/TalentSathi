<template>
  <div class="profile">
    <h1>Profile</h1>
    <form @submit.prevent="updateProfile">
      <input v-model="name" type="text" placeholder="Name" required />
      <input v-model="email" type="email" placeholder="Email" required />
      <button type="submit">Update Profile</button>
    </form>
    <button @click="deleteAccount">Delete Account</button>
  </div>
</template>

<script>
import { useAuthStore } from '../stores/auth';

export default {
  name: 'UserProfile',
  computed: {
    name: {
      get() {
        const authStore = useAuthStore();
        return authStore.user.name;
      },
      set(value) {
        const authStore = useAuthStore();
        authStore.user.name = value;
      }
    },
    email: {
      get() {
        const authStore = useAuthStore();
        return authStore.user.email;
      },
      set(value) {
        const authStore = useAuthStore();
        authStore.user.email = value;
      }
    }
  },
  methods: {
    updateProfile() {
      const authStore = useAuthStore();
      authStore.updateProfile({ name: this.name, email: this.email });
    },
    deleteAccount() {
      const authStore = useAuthStore();
      authStore.deleteAccount();
    }
  }
};
</script>
