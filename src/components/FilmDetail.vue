<template lang="html">
  <article v-if="film">
      <h3> {{ film.title }}</h3>
      <dl>
        <dt>Description:</dt>
      <dd>{{ film.description }}</dd>

      <dt>Released:</dt>
      <dd>{{ film.release_date }}</dd>

      <dt>Director:</dt>
      <dd>{{ film.director }}</dd>

      <dt>Producer:</dt>
      <dd>{{ film.producer }}</dd>
      </dl>
    </article>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'film-detail',
  props: ['film']
}
</script>

<style lang="css" scoped>
</style>
