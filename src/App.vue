<template>
  <div class="container mt-4">
    <h1 class="text-center mb-4">Mis Películas <img src="/public/pelicula.png" ></h1>
    

    <BarraBusqueda @al-buscar="buscarPeliculas" />

    <div class="row mt-4">
      <TarjetaPelicula
        v-for="pelicula in peliculas"
        :key="pelicula.imdbID"
        :pelicula="pelicula"
        @mas-info="mostrarModal"
      />
    </div>

    <ModalPelicula
      v-if="peliculaSeleccionada"
      :pelicula="peliculaSeleccionada"
      @cerrar="peliculaSeleccionada = null"
    />
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import BarraBusqueda from './components/BarraBusqueda.vue'
import TarjetaPelicula from './components/TarjetaPelicula.vue'
import ModalPelicula from './components/ModalPelicula.vue'

const cargarPeliculasIniciales = async () => {
  try {
    const url = `http://www.omdbapi.com/?apikey=bc465282&s=2025`
    const respuesta = await fetch(url)
    const datos = await respuesta.json()
    peliculas.value = datos.Search || []
  } catch (error) {
    console.error('Error al cargar películas iniciales:', error)
  }
}

onMounted(() => {
  cargarPeliculasIniciales()
})

const peliculas = ref([])
const peliculaSeleccionada = ref(null)

const buscarPeliculas = async ({ titulo, tipo, anio }) => {
  try {
    const url = `http://www.omdbapi.com/?apikey=bc465282&s=${titulo}&type=${tipo}&y=${anio}`
    const respuesta = await fetch(url)
    const datos = await respuesta.json()
    peliculas.value = datos.Search || []
  } catch (error) {
    console.error('Error al buscar películas:', error)
  }
}

const mostrarModal = async (idImdb) => {
  try {
    const respuesta = await fetch(`http://www.omdbapi.com/?apikey=bc465282&i=${idImdb}`)
    const datos = await respuesta.json()
    peliculaSeleccionada.value = datos
  } catch (error) {
    console.error('Error al cargar detalles:', error)
  }
}


</script>
