<template>
    <div class="page q-pa-md q-gutter-md">
      
      <div class="list">
        <MovieList />
      </div>
    </div>
  </template>
  <style scoped>
  .page {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
  }
  
  .filter {
    flex: 0 0 300px;
    margin-right: 16px;
  }
  
  .list {
    flex: 1;
  }
  </style>
  <script>
  

import MovieList from "src/components/movie/MovieList.vue";
  export default {
    name: "MoviePage",
    components: {
    MovieList
},
  };
  </script>