<template>
  <article>
    <h2>{{podcast.collectionName}}</h2>

    <img :alt="podcast.collectionName" :src="podcast.artworkUrl600" />
  </article>
</template>

<script>
export default {
  props: ['podcast']
}
</script>

<style scoped>
article {
  background: #fff;
  align-items: center;
  border-radius: 0.4em;
  box-shadow: 0 0 0.4em #aaa;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

article > button {
  background: linear-gradient(45deg, #ff4136, #0074d9);
  border: 0;
  border-radius: 0 0 0.25em 0.25em; /* 0 0 4px 4px */
  color: #fff;
  cursor: pointer;
  padding: 0.75em 0; /* 12px 0 */
  width: 100%;
}

article > h2 {
  font-size: 2rem;
  margin: 0.3em 0.5em 0.3em; /* 6px 10px 6px */
  text-align: center;
}

article > img {
  margin-bottom: 0.6em;
  width: 50%;
}
</style>
