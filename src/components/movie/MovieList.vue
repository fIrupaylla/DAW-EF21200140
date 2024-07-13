<template>
    <div class="movie-list">
      <div class="movie-grid">
        <!-- Aqui empieza mi contenedor -->
        <div class="movie-image" v-for="row in arregloMovie" :key="row.id">
          <!-- Aqui empieza mi q-card -->
          <q-card class="movie-card" >
            <q-card-section class="image-container">
              <q-img :src="row.backdrop_path" alt="" class="image-content"></q-img>
            </q-card-section>
            <q-card-section>
              <div class="text-h6 font-weight-bold">
                <q-card-title class="custom-title">{{ row.original_name }}</q-card-title>
                
              </div>
            </q-card-section>
          </q-card>
          <!-- Aqui acaba para el IF -->
        </div>
        <!-- Aqui acaba mi contenedor -->
      </div>
    </div>
  </template>
  
  <style>
  .nasa-list {
    background-color: #f5f5f5; /* Opcional: color de fondo */
    border-radius: 8px; /* Opcional: bordes redondeados */
  }
  .nasa-image {
    margin-bottom: 20px;
  }
  
  .nasa-card {
    width: 100%;
    height: 300px;
    display: flex;
    flex-direction: column;
  }
  
  .image-container {
    height: 70%;
    overflow: hidden;
  }
  
  .image-content {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  
  .custom-title {
    color: #666; /* Tono rojo */
    font-family: Arial, Helvetica, sans-serif;
    font-weight: bold;
    text-transform: uppercase;
    font-size: 14px;
  }
  .text-h5 {
    color: #555; /* Tono rojo */
    font-family: Arial, Helvetica, sans-serif;
    font-size: 12px;
    font-style: italic;
  }
  
  .nasa-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 10px;
  }
  </style>
  
  <script>
  export default {
    name: "MovieList",
    components: {},
    data() {
      return {
        arregloMovie: [],
      };
    },
    mounted() {
      this.loadImages();
    },
    methods: {
      loadImages() {
        var URL = " ";
        var token = "eyJhbGciOiJIUzI1NiJ9.eyJhdWQiOiJjODRmMmUwODYxM2JmN2FlYTM1OGI0OTgzNDNkMWUwNiIsInN1YiI6IjVmZTUxM2M3ZTE4Yjk3MDAzYzg5NzE3MCIsInNjb3BlcyI6WyJhcGlfcmVhZCJdLCJ2ZXJzaW9uIjoxfQ.StJwmra-PsBwZTOXWg3Y06VEu8CGfAo8dXV7ZQ3RnIs";
  
        var vinclude_adult = false;
        var vpage = "1";
        var vlanguage = "en-US";
  
       
        this.$api
          .get(URL, {
            params: {
              api_key: token,
              include_adult: vinclude_adult,
              page: vpage,
              language: vlanguage,
            },
          })
          .then((response) => {
            this.arregloMovie = response.data;
            console.log(JSON.stringify(response));
          })
          .catch((error) => {
            console.log("Ocurrio un Error: ");
          });
      },
  
      
    },
  };
  </script>
  