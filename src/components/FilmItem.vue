<template>
    <li :class="{ 'film-item': true, 'selected': isSelected }">
      {{ film.title }} - {{ film.director }} ({{ film.genre }})
      <button @click="selectFilm" class="select-button">Pilih</button>
    </li>
  </template>
  
  <script>
  export default {
    props: {
      film: Object,
      isSelected: Boolean
    },
    methods: {
      selectFilm() {
        this.$emit('select-film', this.film);
      }
    }
  };
  </script>
  
  <style scoped>
  .film-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    padding: 10px;
    margin: 5px 0;
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 4px;
    transition: background-color 0.3s, color 0.3s;
  }
  .film-item:hover {
    background-color: #e2e8f0;
  }
  .selected {
    background-color: #b1cef9;
    color: #fff;
    border-color: #8ea9e4;
  }
  .select-button {
    padding: 5px 10px;
    background-color: #16378b;
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: background-color 0.3s;
  }
  .select-button:hover {
    background-color: #8eafd3;
  }
  </style>
  