<template>
    <div class="col-md-3 mb-4">
      <div class="card h-100">
        <img :src="pelicula.Poster" class="card-img-top" :alt="pelicula.Title" />
        <div class="card-body">
          <h5 class="card-title">{{ pelicula.Title }}</h5>
          <p class="card-text">{{ pelicula.Year }} | {{ pelicula.Type }}</p>
          <button class="btn btn-sm btn-info" @click="$emit('mas-info', pelicula.imdbID)">Más información</button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  defineProps(['pelicula'])
  defineEmits(['mas-info'])
  </script>
  