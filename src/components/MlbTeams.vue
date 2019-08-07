<template>
  <div>
    <h1>{{ title }}</h1>
    <div class="card" v-for='(item, index) in teams'>
      <div>Team: <input v-model="item.teamName"></div>
      <div>City: <input v-model="item.City"></div>
      <div>State: <input v-model="item.State"></div>
      <div>League: <input v-model="item.League"></div>
      <div>WorldSeries Wins: <input v-model='item.worldSeriesTitles'></div>
      <button @click="submit(item)">Update</button>
      <button @click="deleteTeam(item.teamId)">Delete</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'MlbTeams',
  data: function() {
    return {
      title: 'Current Teams',
      teams: []
    }
  },
  methods: {
    teamList() {
      axios.get('http://localhost:3000/teams')
    .then( (response) => {
      // handle success
      console.log(response);
      this.teams = response.data;
    })
    .catch(function (error) {
      // handle error
      console.log(error);
    })
    .finally(function () {
      // always executed
    });
  },
  submit(item) {
    axios.put(`http://localhost:3000/update/`,item)
    .then( (response) => {
      // handle success
      console.log(response);
      // this.employees = response.data;
    })
    .then( (response) => {
      this.teamList()
      // console.log(response);
    })
    .catch(function (error) {
      // handle error
      console.log(error);
    })
  },
  deleteTeam(id) {
    axios.delete(`http://localhost:3000/delete/${id}`)
    .then( (response) => {
      // handle success
      console.log(response);
      // this.employees = response.data;
    })
    .then( (response) => {
      this.teamList()
      // console.log(response);
    })
    .catch(function (error) {
      // handle error
      console.log(error);
    })
  }
  },
  created() {
    this.teamList();
  }
  }

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
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
  text-align: center;
  max-width: 60%;
  border: solid 1px #000000;
  border-radius: 10px;
  margin: .8em auto;
  min-height: 200px;
}
.card div {
  padding: .3em;

}
button {
  margin: .3em;
}
</style>
