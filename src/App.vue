<script setup>
import 'bootstrap/dist/css/bootstrap.min.css';
import Navbar from './common/Navbar.vue';
import { RouterView } from 'vue-router';
</script>

<template>
  <Navbar />

  <div class="container-fluid">
    <RouterView />
  </div>
</template>