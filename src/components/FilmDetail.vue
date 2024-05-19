<template>
    <div v-if="film" class="film-detail">
      <h2>Detail Film</h2>
      <p><strong>Judul:</strong> {{ film.title }}</p>
      <p><strong>Sutradara:</strong> {{ film.director }}</p>
      <p><strong>Genre:</strong> {{ film.genre }}</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      film: Object
    }
  };
  </script>
  
  <style scoped>
  .film-detail {
    padding: 20px;
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 8px;
    margin-top: 20px;
  }
  .film-detail h2 {
    color: #9ac5e0;
  }
  </style>
  