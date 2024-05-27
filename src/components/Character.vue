<script setup>
import { defineProps, defineEmits } from 'vue';
defineProps(['character']);
const emit = defineEmits();

const showMore = (id) => {
  emit("showModal", id);
};
</script>

<template>
  <div class="col-6 col-sm-4 col-md-3 col-lg-2 mb-3">
    <div class="card h-100">

      <img :src="character.image" class="card-img-top" alt="...">
      <div class="card-body p-2">
        <!-- <p class="card-text">
          {{ character.gender }} | {{ character.species }} | {{ character.status }}
        </p> -->

        <button type="button"
          class="btn btn-outline-info w-100"
          data-toggle="modal"
          data-target="#evilModal"
          @click="showMore(character.id)">
          {{ character.name }}
        </button>
      </div>

    </div>
  </div>
</template>