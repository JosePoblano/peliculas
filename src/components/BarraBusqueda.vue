<template>
    <form @submit.prevent="emitirBusqueda" class="row g-2">
      <div class="col-md-4">
        <input v-model="titulo" type="text" class="form-control" placeholder="Título" required />
      </div>
      <div class="col-md-2">
        <select v-model="tipo" class="form-select">
          <option value="">Tipo</option>
          <option value="movie">Película</option>
          <option value="series">Serie</option>
          <option value="episode">Episodio</option>
        </select>
      </div>
      <div class="col-md-2">
        <input v-model="anio" type="number" class="form-control" placeholder="Año" />
      </div>
      <div class="col-md-2">
        <button class="btn btn-primary w-100">Buscar</button>
      </div>
    </form>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const emitir = defineEmits(['al-buscar'])
  
  const titulo = ref('')
  const tipo = ref('')
  const anio = ref('')
  
  const emitirBusqueda = () => {
    emitir('al-buscar', {
      titulo: titulo.value,
      tipo: tipo.value,
      anio: anio.value,
    })
  }
  </script>
  