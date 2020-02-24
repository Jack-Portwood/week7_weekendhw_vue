<template lang="html">
    <div>
        <label> Select a Team:</label>
        <!-- <ul>
            <list-item v-for="(team, index) in teams" :team ="team"
            :key="index"></list-item>
            </ul>  -->
        </div>



<!-- <form v-on:submit.prevent> -->
    <!-- <input type="text" v-model="search" placeholder="Whit's yer big team..?"
    v-on:keyup="searchForTeam"
    <select v-on:change="handleClick" v-model="selectedTeam">
        <option disable value="">Whit's yer big team...</option>
        <option v-for="team,index) in teams" :team="team" :key="index">{{team}}</option>
    </select>
</form>   -->
</template>

<script>
import ListItem from './ListItem.vue';


export default {
    name: 'team-list',
    props: ['teams'],
    components: {
        "list-item": ListItem
        },
    methods:{


    }
}
</script>

<style>

</style>