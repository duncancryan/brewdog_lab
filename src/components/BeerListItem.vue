<template>
<li>
  <p>{{favouriteBeer.name}}</p>
  <button v-on:click="handleClick">Delete Beer</button>
</li>
</template>

<script>
import { eventBus } from "../main.js"
export default {
    name: 'beer-list-item',
    props: ['favouriteBeer'],
    methods: {
        handleClick: function(){
            eventBus.$emit('beer-deleted', this.favouriteBeer)
        }
    }
}
</script>

<style>
li{
    margin-top: 10px;
}
</style>