<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import Character from '../components/Character.vue';

const characters = ref([]);
const page       = ref(1);
const pages      = ref(1);

const changePage = (goToPage) => {
  page.value = (goToPage <= 0 || goToPage > pages) ? page : goToPage;
  getData();
};
const getData = async () => {
  try {
    const res = await axios.get("https://rickandmortyapi.com/api/character/"+(page.value !== 0 ? `?page=${ page.value }` : ''));
    if (res.status !== 200)
      throw ("Error al consultar");

    characters.value = res.data.results;
    pages.value = res.data.info.pages;
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

  <nav aria-label="Page navigation example">
    <ul class="pagination">

      <li class="page-item">
        <a class="page-link" href="#" aria-label="Previous" @click="changePage(page-1)">
          <span aria-hidden="true">&laquo;</span>
        </a>
      </li>

      <li class="page-item"><a class="page-link" href="#">{{ page }}</a></li>
      <!-- <li class="page-item"><a class="page-link" href="#">2</a></li> -->
      <!-- <li class="page-item"><a class="page-link" href="#">3</a></li> -->

      <li class="page-item">
        <a class="page-link" href="#" aria-label="Next" @click="changePage(page+1)">
          <span aria-hidden="true">&raquo;</span>
        </a>
      </li>

    </ul>
  </nav>
</template>