<script setup>
import { RouterLink, RouterView } from 'vue-router'
import 'bootstrap/dist/css/bootstrap.min.css'
</script>

<template>
  <nav class="navbar navbar-expand navbar-dark bg-dark">
    <a class="navbar-brand" href="#">Navbar</a>

    <div class="collapse navbar-collapse">
      <ul class="navbar-nav ml-auto">
        <li class="nav-item">
          <RouterLink to="/" class="nav-link">Home</RouterLink>
        </li>

        <li class="nav-item">
          <RouterLink to="/about" class="nav-link">About</RouterLink>
        </li>
      </ul>
    </div>
  </nav>

  <div class="container">
    <RouterView />
  </div>
</template>