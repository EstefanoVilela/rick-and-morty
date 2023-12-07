<script setup>
import { defineProps } from 'vue';
defineProps(['character']);
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
        <a href="#" class="btn btn-primary w-100">Ver</a>
      </div>

    </div>
  </div>
</template>