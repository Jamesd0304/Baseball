<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/mlb-logo.png">
    <MlbTeams/>
    <NewTeam/>
  </div>
</template>

<script>
import MlbTeams from './components/MlbTeams.vue'
import NewTeam from './components/NewTeam.vue'
export default {
  name: 'app',
  components: {
    MlbTeams,
    NewTeam
  }
}
</script>

<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
img {
  max-width: 250px;
  max-height: 250px;
}
</style>
