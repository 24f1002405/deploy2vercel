<script setup>
import HelloWorld from './components/HelloWorld.vue';
import { ref } from 'vue';

const randomNumber = ref(null);

async function fetchRandomNumber() {
  try {
    const response = await fetch('/api/random');
    const data = await response.json();
    randomNumber.value = data.number;
  } catch (err) {
    console.error("Error fetching random number:", err);
  }
}

</script>

<template>
  <div>
    <a href="https://vite.dev" target="_blank">
      <img src="/vite.svg" class="logo" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
    </a>
  </div>
  <button @click="fetchRandomNumber">Get Random Number</button>
  <p v-if="randomNumber">Random Number: {{ randomNumber }}</p>
  <HelloWorld msg="Vite + Vue + Rajat" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}

.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}

.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
