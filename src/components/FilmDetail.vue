<template lang="html">
  <article v-if="film">
    <h3> "{{ film.title }}"</h3>
    <p> {{ film.description }} </p>
    <p>Released: {{ film.release_date }}</p>
    <p>Director: {{ film.director }}</p>
    <p>Producer: {{ film.producer }}</p>

    <button v-on:click="handleFavouriteFilm" type="submit" name="button" >Add to favourites</button>
    <button v-on:click="handleDeleteFavouriteFilm" type="submit" name="button" >Remove from favourites</button>

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
    },
    handleDeleteFavouriteFilm() {
      eventBus.$emit('favourite-film-deselected', this.film)
    }
  }
}
</script>

<style lang="css" scoped>

button {
background-color: #fee2bd;
  color: #0a0180;
  margin: 0.7rem 0.7rem;
  padding: 0.8rem 0.8rem;
  margin-top: 1rem;
  font-size: 16px;
  border: 1px solid;
  border-color: #0a0180;
}

button:hover {
  background-color: #ff9100;
  color: #02001d;
  transition: all 0.5s ease;

}

h3 {
  margin-left: 20px;
  color: #0a0180;
  font-weight: bold;
}

p {
  margin-left: 20px;
  margin-right: 40px;
  font-size: 18px;
}

</style>
