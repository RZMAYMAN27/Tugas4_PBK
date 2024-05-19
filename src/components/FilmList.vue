<template>
    <div class="film-list">
      <h2>Daftar Film Indonesia</h2>
      <ul>
        <FilmItem 
          v-for="film in films" 
          :key="film.id" 
          :film="film" 
          :is-selected="film.id === selectedFilmId"
          @select-film="selectFilm"
        />
      </ul>
      <slot name="detail"></slot>
    </div>
  </template>
  
  <script>
  import FilmItem from './FilmItem.vue';
  
  export default {
    components: { FilmItem },
    data() {
      return {
        films: [
          { id: 1, title: 'Laskar Pelangi', director: 'Riri Riza', genre: 'Drama' },
          { id: 2, title: 'Ada Apa Dengan Cinta?', director: 'Rudi Soedjarwo', genre: 'Romance' },
          { id: 3, title: 'Pengabdi Setan', director: 'Joko Anwar', genre: 'Horror' }
        ],
        selectedFilmId: null
      };
    },
    methods: {
      selectFilm(film) {
        this.selectedFilmId = film.id;
        this.$emit('film-selected', film);
      }
    }
  };
  </script>
  
  <style scoped>
  .film-list {
    padding: 20px;
    background-color: #f3f4f6;
    border: 1px solid #ddd;
    border-radius: 8px;
  }
  .film-list h2 {
    color: #7997d7;
  }
  .film-list ul {
    list-style-type: none;
    padding: 0;
  }
  </style>
  