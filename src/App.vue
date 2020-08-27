<template>
  <div id="app">    
    <h1>BrewDog Archive</h1>
    <label for="beer_select">Which Beer?</label>
    <select id="beer_select" v-model="selectedBeer">
      <option disabled value="">Select a Beer</option>
      <option v-for="(beer, index) in beers" :key="index" :value="beer">{{beer.name}}</option>
    </select>
    <button v-if="!favouriteBeers.includes(selectedBeer)" v-on:click="addBeer">Add Beer</button>
    <div id="app-container">

    <beer-detail v-if="selectedBeer" :selectedBeer="selectedBeer">

    </beer-detail>


    <favourite-beers :favouriteBeers="favouriteBeers">

    </favourite-beers>
    </div>
  </div>
</template>

<script>
import BeerDetail from './components/BeerDetail.vue';
import FavouriteBeers from './components/FavouriteBeers.vue';

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
    'favourite-beers': FavouriteBeers
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
#app-container{
  display: flex;
}
beer-detail{
  width: 60%;
}
favourite-beers{
  width: 40%;
  margin-left: 20px;
}
</style>
