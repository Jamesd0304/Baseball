<template>
  <div class="card">
    <h1>{{ title }}</h1>
    <!-- <div>TeamId:<input v-model="newTeam.teamId"></div> -->
    <div>Team:<input v-model="newTeam.teamName"></div>
    <div>City:<input v-model="newTeam.City"></div>
    <div>State::<input v-model="newTeam.State"></div>
    <div>League:<input v-model="newTeam.League"></div>
    <div>WorldSeries Wins:<input v-model="newTeam.worldSeriesTitles"></div>
    <button @click='addTeam'>Add Team</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'NewTeam',
  data: function() {
    return {
      title: 'Adding a New Team',
      newTeam: {
        // teamId: '',
        teamName: '',
        City: '',
        State: '',
        League: '',
        worldSeriesTitles: ''
      }
    }
  },
  methods: {
    addTeam() {
      axios.post('http://localhost:3000/new',this.newTeam)
      .then( (response) => {
        // handle success
        console.log(response);
        // this.employees = response.data;
      })
      .then( (response) => {
        // this.updateList()
        // console.log(response);
      })
      .catch(function (error) {
        // handle error
        console.log(error);
      })
    }
    // updateList() {
    //   axios.get('http://localhost:3000/employees')
    // .then( (response) => {
    //   // handle success
    //   console.log(response);
    //   this.employees = response.data;
    // })
    // .catch(function (error) {
    //   // handle error
    //   console.log(error);
    // })
    // .finally(function () {
    //   // always executed
    // });
    // }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.card {
  border: solid 1px #000000;
  max-width: 50%;
  margin:.5em auto;
  text-align: center;
}
input {
  margin: .5em;
}
</style>
