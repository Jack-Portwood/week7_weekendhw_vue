<template>
<form>
  <label for="selectedTeam"> Fits Yer Big Team...  </label>
  <select id="selectedTeam" v-on:change="handleChange" v-model="pickedteam">
      <option v-for="(team,index) in teams" :value="team" :key="index">{{team}}</option>
    </select>
</form>
</template>

<script>
import ListItem from './ListItem.vue';
import {eventBus} from '../main.js';
export default {
    name: 'selected-team',
    data(){
        return{
            pickedteam: null 
            
        }
    },
props:['teams'],
methods:{
    handleChange() {
        eventBus.$emit('selected-team', this.pickedteam);
    }
}
}
</script>

<style>

</style>