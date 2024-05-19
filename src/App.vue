<template>
  <div id="app" class="app-container">
    <FilmList @film-selected="showFilmDetail">
      <template v-slot:detail>
        <FilmDetail :film="selectedFilm" />
        <button v-if="selectedFilm" @click="saveFilm" class="save-button">Simpan Film</button>
      </template>
    </FilmList>
    <div class="saved-films" v-if="savedFilms.length > 0">
      <h2>Daftar Film yang Disimpan</h2>
      <ul>
        <li v-for="film in savedFilms" :key="film.id">
          {{ film.title }} - {{ film.director }} ({{ film.genre }})
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import FilmList from './components/FilmList.vue';
import FilmDetail from './components/FilmDetail.vue';

export default {
  components: { FilmList, FilmDetail },
  data() {
    return {
      selectedFilm: null,
      savedFilms: []
    };
  },
  methods: {
    showFilmDetail(film) {
      this.selectedFilm = film;
    },
    saveFilm() {
      if (this.selectedFilm && !this.savedFilms.some(film => film.id === this.selectedFilm.id)) {
        this.savedFilms.push(this.selectedFilm);
      }
    }
  }
};
</script>

<style>
.app-container {
  font-family: 'Arial', sans-serif;
  margin: 20px;
  padding: 20px;
  background-color: #0e3967;
  border-radius: 8px;
  max-width: 600px;
  margin: 0 auto;
}
.save-button {
  display: block;
  margin-top: 20px;
  padding: 10px;
  background-color: #65a7da;
  color: rgb(30, 43, 58);
  border: none;
  border-radius: 4px;
  cursor: pointer;
  transition: background-color 0.3s;
}
.save-button:hover {
  background-color: #eef6ff;
}
.saved-films {
  margin-top: 40px;
}
.saved-films h2 {
  color: #bdc3d0;
}
.saved-films ul {
  list-style-type: none;
  padding: 0;
}
.saved-films li {
  padding: 10px;
  background-color: #aebcdf;
  border: 1px solid #9ac0d9;
  border-radius: 4px;
  margin: 5px 0;
}
</style>
