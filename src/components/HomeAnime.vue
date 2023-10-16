<template>
  <div class="container">
    <FormSearch @onSearchAnime="onSearchAnime" />
    <div class="anime">
      <a
        :href="anime.url"
        target="_blank"
        class="item"
        v-for="anime in animes?.data"
        :key="anime.mail_id"
      >
        <div class="card">
          <div class="wrapper">
            <img :src="anime.images.jpg.image_url" class="cover-image" />
          </div>
          <p class="title">{{ anime.title }}</p>
        </div>
      </a>
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
.container {
  text-align: center;
}
.anime {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-wrap: wrap;
}
@media screen and (min-width: 1024px) {
  .item {
    height: 300px;
    padding: 1rem;
    width: 15%;
  }
  .card {
    border-radius: 15px;
  }
}
@media screen and (min-width: 768px) {
  .item {
    height: 200px;
    padding: 1rem;
    width: 20%;
  }
  .card {
    border-radius: 10px;
  }
}
@media screen and (min-width: 548px) {
  .item {
    height: 200px;
    padding: 1rem;
    width: 45%;
  }
}
@media screen and (max-width: 548px) {
  .item {
    height: 200px;
    padding: 1rem;
    width: 95%;
  }
  .card {
    border-radius: 5px;
  }
}
.card {
  width: 100%;
  height: 100%;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: flex-end;
  overflow: hidden;
  border: 1px solid black;
  cursor: pointer;
}
.wrapper {
  height: 100%;
  width: 100%;
  object-fit: cover;
}
.cover-image {
  width: 100%;
  height: 300px;
  object-fit: cover;
}
.title {
  position: absolute;
  margin: 0;
  right: 0;
  left: 0;
  bottom: 0%;
  padding: 1rem;
  text-align: center;
  transition: all 0.1s ease-in-out;
  font-size: 1.2rem;
  font-weight: bold;
  color: rgb(255, 170, 0);
  /* background: #000; */
}
.card:hover .title {
  transform: translateY(-40px);
}
</style>
