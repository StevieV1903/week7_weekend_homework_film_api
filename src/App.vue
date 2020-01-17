<template>
  <div id="app">
    <h1>Studio Ghibli Films</h1>
    <div class="main-container">
      <all-films-list :films='films'></all-films-list >
        <film-detail :film="selectedFilm"></film-detail >
    </div>
  </div>
</template>

<script>

import {eventBus} from './main.js'
import AllFilmsList from './components/AllFilmsList.vue'
import FilmDetail from './components/FilmDetail.vue'

export default {
  name: 'app',
  data() {
    return {
      films: [],
      selectedFilm: null
    }
  },

  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
      .then( response => response.json() )
      .then( films => this.films = films )

      eventBus.$on('film-selected', (film)=> {
              this.selectedFilm = film
            })

  },

  components: {
    "all-films-list": AllFilmsList,
    "film-detail": FilmDetail
  }
}
</script>



<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.main-container {
          display: flex;
          justify-content: space-between;
        }
</style>
