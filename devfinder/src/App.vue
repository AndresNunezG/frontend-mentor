<template>
  <div class="app-container bg-primary fg-primary">
    <h1>devfinder</h1>
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
import Profile from './components/Profile.vue'
import Loader from './components/Loader.vue'
import './assets/css/main.css'

const apiUrl = 'https://api.github.com/users/'
const testUser = 'AndresNunezG'

export default {
  name: 'App',
  components: {
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