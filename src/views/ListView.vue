<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import Character from '../components/Character.vue';

const characters = ref([]);
const getData = async () => {
  try {
    const res = await axios.get("https://rickandmortyapi.com/api/character/");
    if (res.status !== 200)
      throw ("Error al consultar");

    characters.value = res.data.results;
  } catch (error) {
    alert(error);
  }
};

onMounted(() => {
  getData();
})
</script>

<template>
  <div class="row py-5">
    <div class="col-md-12">
      <h5 class="text-center">Rick and Morty</h5>
      <hr>
    </div>

    <Character v-for="character of characters" :key="character.id" :character="character" />
  </div>
</template>