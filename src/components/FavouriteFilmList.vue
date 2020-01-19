<template lang="html">
  <div>
    <h3>Favourite Films;</h3>
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

h3 {
  margin-left: 20px;
  color: #0a0180;
}

ul {
  font-size: 18px;
}
</style>
