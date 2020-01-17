<template lang="html">
  <div>
      <ul>
        <film-list-item v-for="(film) in films" :film="film"></film-list-item>
      </ul>
    </div>
</template>

<script>
import {eventBus} from '../main.js'
import FilmListItem from './FilmListItem.vue'

export default {
  name: 'all-films-list',
  props: ['films'],
  methods: {
  },
  components: {
    "film-list-item": FilmListItem
  }
}

</script>

<style lang="css" scoped>
</style>
