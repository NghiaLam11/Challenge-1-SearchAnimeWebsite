<template>
  <div class="form-search">
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

<style scoped>
.form-search {
  margin-top: 5rem;
  margin-bottom: 2rem;
}
form input, button {
  font-size: 1.3rem;
  padding: 0.5rem 0.3rem;
  cursor: pointer;
}
</style>
