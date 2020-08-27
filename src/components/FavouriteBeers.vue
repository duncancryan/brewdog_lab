<template>
  <div>
      <ul>
      <h2>My Favourite Brews</h2>
          <li v-for="favouriteBeer in favouriteBeers">{{favouriteBeer.name}}</li>
      </ul>

  </div>
</template>

<script>
export default {
    name: 'favourite-beers',
    props: ['favouriteBeers']
}
</script>

<style scoped>
ul{
    list-style: none;
}
li{
    margin-top: 10px;
}
</style>