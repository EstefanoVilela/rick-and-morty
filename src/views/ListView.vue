<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import Character from '../components/Character.vue';
import Modal from '../common/Modal.vue';

const characters = ref([]);
const page       = ref(1);
const pages      = ref(1);
const search     = ref("");
const currentCharacter = ref({});

const changePage = (goToPage) => {
  page.value = (goToPage <= 0 || goToPage > pages) ? page : goToPage;
  getData();
};
const searchData = () => {
  page.value = 1;
  getData();
};
const getData = async () => {
  try {
    const res = await axios.get(`https://rickandmortyapi.com/api/character/?page=${ page.value }&name=${ search.value }`);
    if (res.status !== 200)
      throw ("Error al consultar");

    characters.value = res.data.results;
    pages.value = res.data.info.pages;
  } catch (error) {
    alert(error);
  }
};
const showModal = async(id) => {
  try {
    const res = await axios.get(`https://rickandmortyapi.com/api/character/${ id }`);
    if (res.status !== 200)
      throw ("Error al consultar");

    console.log(res.data)
    currentCharacter.value = res.data;
  } catch (error) {
    alert(error);
  }
};

onMounted(() => getData());
</script>

<template>
  <Modal :character="currentCharacter" />
  <div class="row justify-content-center">
    <div class="col-10 col-md-6 col-lg-4 my-3">

      <div class="input-group mb-3">
        <input type="text" class="form-control" placeholder="Buscar un personaje" @keyup.enter="searchData" v-model="search">
        <div class="input-group-append">
          <button class="btn btn-primary" type="button" @click="searchData">Buscar</button>
        </div>
      </div>

    </div>
  </div>

  <div class="row">
    <Character
      v-for="character of characters"
      :key="character.id"
      :character="character"
      @showModal="showModal" />
  </div>

  <nav aria-label="Page navigation example">
    <ul class="pagination">

      <li v-if="page > 1" class="page-item">
        <a class="page-link" href="#" aria-label="Previous" @click="changePage(page - 1)">
          <span aria-hidden="true">&laquo;</span>
        </a>
      </li>

      <li class="page-item">
        <a class="page-link" href="#">{{ page }}</a>
      </li>

      <li class="page-item">
        <a class="page-link" href="#" aria-label="Next" @click="changePage(page + 1)">
          <span aria-hidden="true">&raquo;</span>
        </a>
      </li>

    </ul>
  </nav>
</template>