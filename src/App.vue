<script setup>
import HomeAnime from "./components/HomeAnime.vue";
</script>

<template>
  <HomeAnime />
</template>

<style scoped>
#app {
  display: flex;
  justify-content: center;
  align-items: flex-start;
}
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
