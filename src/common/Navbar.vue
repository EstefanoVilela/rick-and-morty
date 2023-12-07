<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
  <nav class="navbar navbar-expand navbar-dark bg-dark">
    <RouterLink to="#" class="navbar-brand">Navbar</RouterLink>

    <div class="collapse navbar-collapse">
      <ul class="navbar-nav ml-auto">
        <li class="nav-item">
          <RouterLink to="/" class="nav-link">List</RouterLink>
        </li>

        <!-- <li class="nav-item">
          <RouterLink to="/about" class="nav-link">About</RouterLink>
        </li> -->
      </ul>
    </div>
  </nav>
</template>