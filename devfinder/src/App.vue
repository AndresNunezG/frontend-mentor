<template>
  <div class="app-container bg-secondary fg-primary">
    <h1>devfinder</h1>
    <div class="searchbar-container">
      <Searchbar />
    </div>
    <div v-if="fetchingData">
      <Loader/>
    </div>
    <div v-else>
      <Profile :userData="userData" />
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Searchbar from './components/Searchbar.vue'
import Profile from './components/Profile.vue'
import Loader from './components/Loader.vue'
import './assets/css/main.css'

const apiUrl = 'https://api.github.com/users/'
const testUser = 'AndresNunezG'

export default {
  name: 'App',
  components: {
    Searchbar,
    Profile,
    Loader,
  },
  data() {
    return {
      userData: null,
      fetchingData: true,
      errored: false,
    }
  },
  mounted() {
    axios.get(apiUrl + testUser)
    .then(response => (this.userData = response.data))
    .catch(error => {
      console.log(error)
      this.errored = true
    })
    .finally(() => this.fetchingData = false)
  }
}
</script>

<style scoped>
.app-container {
  padding: 7em;
}
.searchbar-container {
  min-width: 100%;
  margin: 1em 0;
}
</style>