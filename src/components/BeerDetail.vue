<template>
  <div id="selected_beer">
      <h2>{{selectedBeer.name}}</h2>
      <h3>{{selectedBeer.tagline}}</h3>
      <p>{{selectedBeer.abv}}% abv.</p>
      <p>{{selectedBeer.description}}</p>
      <img :src="selectedBeer.image_url" alt="beer_image">
  </div>
</template>

<script>
export default {
    name:'beer-detail',
    props:['selectedBeer']
}
</script>

<style>

</style>