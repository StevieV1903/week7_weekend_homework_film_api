<template lang="html">
  <article v-if="film">
    <h3> {{ film.title }}</h3>
    <p>Description: {{ film.description }} </p>
    <p>Released: {{ film.release_date }}</p>
    <p>Director: {{ film.director }}</p>
    <p>Producer: {{ film.producer }}</p>

    <button v-on:click="handleFavouriteFilm" type="submit" name="button" >Add to favourites</button>
    <!-- <button v-on:click="handleDeleteFavouriteFilm" type="submit" name="button" >Remove favourite</button> -->

  </article>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'film-detail',
  props: ['film'],
  methods: {
  handleFavouriteFilm() {
      eventBus.$emit('favourite-film-selected', this.film)
    }
    // handleDeleteFavouriteFilm() {
    //   eventBus.$emit('favourite-film-deselected', this.film)
    // }
}
}
</script>

<style lang="css" scoped>
</style>
