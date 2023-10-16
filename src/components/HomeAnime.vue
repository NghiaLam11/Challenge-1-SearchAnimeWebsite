<template>
  <div>
    <FormSearch @onSearchAnime="onSearchAnime" />
    <div class="anime">
      <div class="item" v-for="anime in animes?.data" :key="anime.mail_id">
        <div class="card">
          <div class="wrapper">
            <img :src="anime.images.jpg.image_url" class="cover-image" />
          </div>
          <p class="title">{{ anime.title }}</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script setup>
import { computed, ref } from "vue";
import FormSearch from "./FormSearch.vue";
const animes = computed(() => anime.value);
const anime = ref();
async function onSearchAnime(name) {
  const response = await fetch(
    `https://api.jikan.moe/v4/anime?q=${name}&limit=10`
  );
  anime.value = await response.json();
  console.log(anime.value);
}
</script>
<style scoped>
p {
  color: yellow;
}
.anime {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
.item {
  height: 300px;
  padding: 1rem;
}
</style>
