<template>
  <div id="app">
    <h1>STUDIO GHIBLI FILMS</h1>
    <all-films-list :films='films'></all-films-list >
      <film-detail :film="selectedFilm"></film-detail >
        <favourite-films-list :favourite-films="favouriteFilms"></favourite-films-list >
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
            const listOfFilmById = this.favouriteFilms.map(film => film.id)
            if (!listOfFilmById.includes(film.id)){
              this.favouriteFilms.push(film)
            }
          })
          eventBus.$on('favourite-film-deselected',(film) => {
            const index = this.favouriteFilms.indexOf(film)
            this.favouriteFilms.splice(index)
          })
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
          text-align: left;
          margin: 60px;
          border: 1px solid;
          background-color: #dddddd
        }
        h1 {
          margin-left: 20px;
          text-align: left;
          color: #0a0180;
          font-size: 32px;
        }
      </style>
