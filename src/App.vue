<template>
  <div id="app">    
    <h1>BrewDog Archive</h1>
    <label for="beer_select">Which Beer?</label>
    <select id="beer_select" v-model="selectedBeer">
      <option disabled value="">Select a Beer</option>
      <option v-for="(beer, index) in beers" :key="index" :value="beer">{{beer.name}}</option>
    </select>

    <beer-detail v-if="selectedBeer" :selectedBeer="selectedBeer">

    </beer-detail>

    <button v-on:click="addBeer">Add Beer</button>

    <favourite-beers v-for="(beer, index) in favouriteBeers" :key="index" :beer="beer">

    </favourite-beers>
  </div>
</template>

<script>
import BeerDetail from './components/BeerDetail.vue';

export default {
  name: 'app',
  data(){
    return {
      beers: [],
      selectedBeer: null,
      favouriteBeers: []
    }
  },
  components: {
    'beer-detail': BeerDetail,
  },
  methods: {
    fetchBeers: function(){
      fetch('https://api.punkapi.com/v2/beers')
      .then(response => response.json())
      .then(beers => this.beers = beers)
    },
    addBeer: function() {
      this.favouriteBeers.unshift(this.selectedBeer);
    }
  },
  mounted(){
    this.fetchBeers();
  }
}
</script>

<style>

</style>
