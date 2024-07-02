<script setup>
import axios from 'axios';

async function loginWithGitHub() {
  console.log('Iniciando login com GitHub...')
  try {
    const response = await axios.get('https://git-node.vercel.app/auth/github/');
  

    console.log(response.data);

  }catch(error) {
    console.error('Erro ao iniciar o login com GitHub:', error);
  }
}

</script>

<template>
  <div>
    <button @click="loginWithGitHub">Login com GitHub</button>
  </div>
</template>