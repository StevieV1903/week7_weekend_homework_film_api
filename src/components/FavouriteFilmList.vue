<template lang="html">
  <div>
    <ul>
      <film-list-item v-for="(film) in favouriteFilms" :film="film"></film-list-item>
    </ul>
  </div>
</template>

<script>
import {eventBus} from '../main.js'
import FilmListItem from './FilmListItem.vue'

export default {
  name: 'favourite-films',
  props: ['favouriteFilms'],
  components: {
    "film-list-item": FilmListItem
  }
}
</script>

<style lang="css" scoped>
</style>
