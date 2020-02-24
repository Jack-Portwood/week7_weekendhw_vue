<template lang="html">
<div v-if='team' id="teamList">
    
    <h2>Stuffing the preverbial onion sack🧅 </h2> 
    <h3>{{team}}</h3>

<ul v-for="fixture in fixtures"> 
    <div v-if="fixture.awayTeam.name===team">
        <p> GOALS away {{fixture.score.fullTime.awayTeam}}
        </p>

    </div> 

    <div v-if="fixture.homeTeam.name===team">
        <p>  GOALS at home {{fixture.score.fullTime.homeTeam}}
        </p>

    </div> 
</ul>



<!-- <p> Score: {{fixtures.score.fullTime}} </p> -->

</div>
</div>
  
</template>

<script>
import { eventBus } from '../main.js';

export default {
    name: 'team-detail',
    data(){
        return{
            team: null 

        };
    },
    
    props: ['fixtures'],





mounted(){

eventBus.$on('selected-team',(team) =>{
    this.team = team;
    })
    

    }
 
};
</script>


<style lang="css" scoped>

</style>
