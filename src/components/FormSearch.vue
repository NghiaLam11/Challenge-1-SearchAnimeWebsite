<template>
  <div>
    <form @submit.prevent="onSearch">
      <input v-model="name" placeholder="Ex: One Piece" type="text" />
      <button type="submit">Search</button>
    </form>
  </div>
</template>

<script setup>
import { ref } from "vue";

const emit = defineEmits("onSearchAnime");
const name = ref("");
const onSearch = () => {
  emit("onSearchAnime", name.value);
};
</script>
