<template>
<div class="main-container">
  <div class="user-container">
    <ProfileCard
      @viewdailyall="dailyAll = !dailyAll"
      @viewweeklyall="weeklyAll =! weeklyAll"
      @viewmonthlyall="monthlyAll =! monthlyAll"
    />
  </div>
  <div class="cards-container">
    <TimeCard
      v-for="(category, index) in timeData"
      :category="timeData[index]"
      :key="index"
      :daily="dailyAll"
      :weekly="weeklyAll"
      :monthly="monthlyAll"
    />
  </div>
</div>
</template>

<script>
import ProfileCard from './components/ProfileCard.vue'
import TimeCard from './components/TimeCard.vue'
import timeData from '../data.json'

export default {
  name: 'App',
  components: {
    ProfileCard,
    TimeCard,
  },
  data() {
    return {
      timeData: timeData,
      dailyAll: false,
      weeklyAll: false,
      monthlyAll: false,
    }
  },
}
</script>