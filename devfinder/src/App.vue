<template>
  <div class="app-container bg-secondary fg-primary" :class="theme ? 'dark-theme' : 'light-theme'">
    <div class="app-title-container">
      <h1>devfinder</h1>
      <div class="themebutton-container">
        <ThemeButton :themeActive="theme" @changeTheme="theme = !theme"/>
      </div>
    </div>
    <div class="searchbar-container">
      <Searchbar :error="errored" @doSearch="searchUser"/>
    </div>
    <div v-if="fetchingData">
      <Loader/>
    </div>
    <div v-else>
      <Profile :userData="userData"/>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import Searchbar from './components/Searchbar.vue'
import Profile from './components/Profile.vue'
import Loader from './components/Loader.vue'
import ThemeButton from './components/ThemeButton.vue'
import './assets/css/main.css'

const apiUrl = 'https://api.github.com/users/'
const testUser = 'AndresNunezG'

export default {
  name: 'App',
  components: {
    Searchbar,
    Profile,
    Loader,
    ThemeButton,
  },
  data() {
    return {
      userData: null,
      fetchingData: true,
      errored: false,
      theme: true,
    }
  },
  mounted() {
    this.fetchApi(testUser)
  },
  methods: {
    fetchApi(username) {
      axios.get(apiUrl + username)
      .then(response => {
        this.userData = response.data
        this.errored = false
      })
      .catch(() => this.errorFetching())
      .finally(() => this.fetchingData = false)
    },
    searchUser(username) {
      this.fetchApi(username)
    },
    errorFetching() {
      this.errored = true
      setTimeout(() => {
        this.errored = false
      }, 2000)
    }
  },
}
</script>

<style scoped>
.app-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 100vh;
  padding: 7em;
  transition: 200ms;
}
.app-title-container {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.themebutton-container {
  height: 100%;
  display: flex;
  align-items: flex-end;
}
.searchbar-container {
  min-width: 100%;
  margin: 1em 0;
}
</style>