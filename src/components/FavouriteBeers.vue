<template>
  <div>
      <ul>
      <h2>My Favourite Brews</h2>
          <beer-list-item v-for="(favouriteBeer, index) in favouriteBeers" :key="index" :favouriteBeer="favouriteBeer"></beer-list-item>
      </ul>

  </div>
</template>

<script>
import BeerListItem from './BeerListItem';

export default {
    name: 'favourite-beers',
    props: ['favouriteBeers'],
    components: {
        "beer-list-item": BeerListItem
    }
}
</script>

<style scoped>
ul{
    list-style: none;
}

</style>