<template>
  <li v-on:click="handleClick">{{teams}}</li>
</template>

<script>
import {eventBus} from '../main.js';
export default {
    name: 'list-item',
    props:['teams'],
    methods:{
        handleClick(){
            eventBus.$emit('selected-team', this.teams)
        }
    }

}
</script>

<style>

</style>