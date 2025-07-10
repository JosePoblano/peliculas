<template>
  <div class="modal fade show d-block" tabindex="-1" style="background: rgba(0,0,0,0.5);">
    <div class="modal-dialog modal-lg">
      <div class="modal-content">
        <div class="modal-header">
          <h5 class="modal-title">{{ pelicula.Title }}</h5>
          <button type="button" class="btn-close" @click="$emit('cerrar')"></button>
        </div>
        <div class="modal-body">
          <div class="row">
            <div class="col-md-4">
              <img :src="pelicula.Poster" class="img-fluid" />
            </div>
            <div class="col-md-8">
              <p><strong>Año:</strong> {{ pelicula.Year }}</p>
              <p><strong>Género:</strong> {{ pelicula.Genre }}</p>
              <p><strong>Director:</strong> {{ pelicula.Director }}</p>
              <p><strong>Sinopsis:</strong> {{ pelicula.Plot }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps(['pelicula'])
defineEmits(['cerrar'])
</script>
