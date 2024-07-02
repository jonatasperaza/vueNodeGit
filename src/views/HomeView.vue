<template>
  <div id="app">
    <button @click="loginWithGitHub">Login with GitHub</button>
    <div v-if="user">
      <h2>Welcome, {{ user.login }}</h2>
      <img :src="user.avatar_url" alt="User Avatar" />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';

const user = ref(null);

const loginWithGitHub = () => {
  window.location.href = 'https://git-node.vercel.app/auth/github';
};

const fetchUser = async () => {
  try {
    const response = await axios.get('https://git-node.vercel.app/api/user', { withCredentials: true });
    user.value = response.data.user;
  } catch (error) {
    console.error('User not authenticated', error);
  }
};

onMounted(() => {
  fetchUser();
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  margin-top: 60px;
}
</style>
