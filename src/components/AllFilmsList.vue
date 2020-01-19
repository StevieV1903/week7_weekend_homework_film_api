<template lang="html">
  <div>
    <h2>Select a film:</h2>
    <select v-on:change="handleSelect" v-model="selectedFilm">
          <option disabled value="">Select a film...</option>
          <option v-for="film in films" :value="film">{{film.title}}</option>
          </select>
    </div>
</template>
<!-- <ul>
        <film-list-item v-for="(film) in films" :film="film"></film-list-item>
      </ul> -->

<script>
import {eventBus} from '../main.js'
import FilmListItem from './FilmListItem.vue'

export default {
  name: 'all-films-list',
  props: ['films'],
  methods: {
    handleSelect(){
      this.search = ""
      eventBus.$emit('film-selected', this.selectedFilm)
    }
  },
  components: {
    "film-list-item": FilmListItem
  }
}

</script>

<style lang="css" scoped>

h2 {
  margin-left: 20px;
  color: #0a0180;
}

select {
  margin-left: 20px;
  margin-right: 20px;
  font-size: 16px;
}
</style>
