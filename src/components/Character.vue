<script setup>
import { defineProps, defineEmits } from 'vue';
defineProps(['character']);
const emit = defineEmits();

const showMore = (id) => {
  emit("showModal", id);
};
</script>

<template>
  <div class="col-6 col-sm-4 col-lg-2 mb-3">
    <div class="card">

      <img :src="character.image" class="card-img-top" alt="...">
      <div class="card-body">
        <b class="card-title">{{ character.name }}</b>
        <p class="card-text">
          {{ character.gender }} | {{ character.species }} | {{ character.status }}
        </p>

        <button type="button" class="btn btn-primary w-100" data-toggle="modal" data-target="#evilModal" @click="showMore(character.id)">
          Ver más
        </button>
      </div>

    </div>
  </div>
</template>