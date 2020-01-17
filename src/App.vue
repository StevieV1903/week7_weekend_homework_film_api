<template>
  <div id="app">
    <h1>Studio Ghibli Films</h1>
    <div class="main-container">
      <all-films-list :films='films'></all-films-list >
        <film-detail :film="selectedFilm"></film-detail >
          <favourite-films-list :favourite-films="favouriteFilms"></favourite-films-list >
    </div>
  </div>
</template>

<script>

import {eventBus} from './main.js'
import AllFilmsList from './components/AllFilmsList.vue'
import FilmDetail from './components/FilmDetail.vue'
import FavouriteFilmsList from './components/FavouriteFilmList.vue'

export default {
  name: 'app',
  data() {
    return {
      films: [],
      favouriteFilms: [],
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
      eventBus.$on('favourite-film-selected', (film)=> {
                    const mapOfIds = this.favouriteFilms.map(film => film.id)
                    if (!mapOfIds.includes(film.id)){
                      this.favouriteFilms.push(film)
                    }
                  })
                  // eventBus.$on('favourite-beer-de-selected',(beer) => {
                  //   const index = this.favouriteBeers.indexOf(beer)
                  //     this.favouriteBeers.splice(index)
                  // })
  },

  components: {
    "all-films-list": AllFilmsList,
    "film-detail": FilmDetail,
    "favourite-films-list": FavouriteFilmsList
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
