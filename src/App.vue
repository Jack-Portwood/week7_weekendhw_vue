<template lang= "html">
<div>
  <h1> THE WONDERFUL WORLD OF GOAL💲⚽️ </h1>
  <selected-team :teams="teams"></selected-team>
  <team-detail :fixtures='fixtures'></team-detail>
  
</div>
</template>

<script>
import TeamList from './components/TeamList.vue';
import {eventBus} from './main.js';
import TeamDetail from './components/TeamDetail.vue';
import SelectedTeam from './components/SelectedTeam.vue';
import ListItem from './components/ListItem.vue'; 



export default {
  name:'app',
  data(){
    return{
    fixtures: [],
    teams:[],
    matches: null,
    
    
  };  
},

computed:{
    // filters:function(){
    //   return this.newFixtures = this.fixtures.filter(match=> fixture.teamname=== this.selectedTeam.name)}
},

  components: {
    "team-list": TeamList,
    "team-detail": TeamDetail,
    "selected-team": SelectedTeam
    
  
  },
    

  

  methods: {
    sortTeams: function(club) {
      this.teams.sort((a, b) => {
        return a[club] < b[club] ? -1 : 1;
      });
          
    
    }
  },
    
  
   mounted(){
    fetch('https://api.football-data.org/v2/competitions/PL/matches', {
      method: 'GET',
      headers: {
        'X-Auth-token': '4c173a7f743d4e6f9fb397c37800b000'
      }
    })
    .then(res => res.json())
    .then (fixtures => this.fixtures = fixtures.matches)
    // .then (filteredFixtures=fixtures.matches)
    
  

    .then ( teams => this.teams = [...new Set 
    (this.fixtures.map(x => x.awayTeam.name))].sort())

    
   

    // eventBus.$on('selected-team',(team) =>{
    // this.selectedTeam = team;
    // })



   }
};



    

</script>


<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
