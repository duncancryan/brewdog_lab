<template>
  <div>
      <h2>My Favourite Brews</h2>
      <ul>
          <li>
              <p>{{beer.name}}</p>
          </li>
      </ul>

  </div>
</template>

<script>
export default {
    name: 'favourite-beers',
    props: ['beer']
}
</script>

<style>
ul{
    list-style: none;
}
</style>