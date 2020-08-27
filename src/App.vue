<template>
  <div id="app">    
    <h1>BrewDog Archive</h1>
    <label for="beer_select">Which Beer?</label>
    <select id="beer_select" v-model="selectedBeer">
      <option disabled value="">Select a Beer</option>
      <option v-for="(beer, index) in beers" :key="index" :value="beer">{{beer.name}}</option>
    </select>

    <beer-detail v-if="selectedBeer" :selectedBeer="selectedBeer"></beer-detail>
  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return {
      beers: [],
      selectedBeer: null,
    }
  },
  componenents: {

  },
  methods: {
    fetchBeers: function(){
      fetch('https://api.punkapi.com/v2/beers')
      .then(response => response.json())
      .then(beers => this.beers = beers)
    }
  },
  mounted(){
    this.fetchBeers();
  }
}
</script>

<style>

</style>
