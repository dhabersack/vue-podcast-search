<template>
  <main>
    <h1>Podcast Search</h1>

    <input type="search" v-model="query" />

    <section>
      <podcast :podcast="podcast" v-for="podcast in podcasts" key="podcast.trackId" />
    </section>
  </main>
</template>

<script>
import Podcast from './Podcast'
import _ from 'lodash'

export default {
  name: 'app',
  data: () => {
    return {
      query: '',
      podcasts: []
    }
  },
  components: {
    'podcast': Podcast
  },
  watch: {
    query: function () {
      this.onQueryChange()
    }
  },
  methods: {
    onQueryChange: _.debounce(function () {
      fetch(`https://itunes.apple.com/search?term=${this.query}&media=podcast`)
          .then((response) => response.json())
          .then((results) => {
            this.podcasts = results.results;
          });
    }, 250)
  }
}
</script>

<style scoped>
section {
  background: #ddd;
  border-bottom: 0.1em solid #fff;
  border-top: 0.1em solid #ccc;
  display: grid;
  grid-template-columns: 1fr;
  grid-column-gap: 2%;
  grid-row-gap: 1.2em;
  padding: 1.1em 2%;
}

@media screen and (min-width: 320px) {
  section {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media screen and (min-width: 640px) {
  section {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media screen and (min-width: 960px) {
  section {
    grid-template-columns: repeat(4, 1fr);
  }
}

@media screen and (min-width: 1280px) {
  section {
    grid-template-columns: repeat(5, 1fr);
  }
}

@media screen and (min-width: 1600px) {
  section {
    grid-template-columns: repeat(6, 1fr);
  }
}
</style>
