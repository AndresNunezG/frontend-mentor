<template>
    <div :class="`${category.title.toLowerCase().replace(' ', '-')}-container br card`">
        <div class="card-header">
            <img :src="icons[category.title.replace(' ', '')]" :alt="category.title">
        </div>
        <div class="subcard br">
            <div class="subcard-header">
                <p class="fw-500">{{ category.title }}</p>
                <button class="btn btn-display-menu" @click="displayMenu = !displayMenu">
                    <img class="more-icon" src="../assets/images/icon-ellipsis.svg" alt="more-icon">
                </button>
                <ul class="card-menu">
                    <li><button @click="viewDaily" class="btn">Daily</button></li>
                    <li><button @click="viewWeekly" class="btn">Weekly</button></li>
                    <li><button @click="viewMonthly" class="btn">Monthly</button></li>
                </ul>
            </div>
            <div class="subcard-body">
                <h2 class="fw-300 fs-xl">{{ current }}hrs</h2>
                <p class="fw-300 fg-sec">Last {{ dateText }} - {{ previous }}hrs</p>
            </div>
        </div>
    </div>
</template>

<script>
import iconWork from '../assets/images/icon-work.svg'
import iconPlay from '../assets/images/icon-play.svg'
import iconStudy from '../assets/images/icon-study.svg'
import iconExercise from '../assets/images/icon-exercise.svg'
import iconSocial from '../assets/images/icon-social.svg'
import iconSelfCare from '../assets/images/icon-self-care.svg'

const iconsDict = {}
iconsDict.Work = iconWork
iconsDict.Play = iconPlay
iconsDict.Study = iconStudy
iconsDict.Exercise = iconExercise
iconsDict.Social = iconSocial
iconsDict.SelfCare = iconSelfCare

export default({
    name: "TimeCard",
    props: {
        category: Object,
        daily: Boolean,
        weekly: Boolean,
        monthly: Boolean,
    },
    data() {
        return {
            icons: iconsDict,
            displayMenu: false,
            current: this.category.timeframes.daily.current,
            previous: this.category.timeframes.daily.previous,
            dateText: "day",
        }
    },
    methods: {
        viewDaily() {
            this.current = this.category.timeframes.daily.current
            this.previous = this.category.timeframes.daily.previous
            this.dateText = "day"
        },
        viewWeekly() {
            this.current = this.category.timeframes.weekly.current
            this.previous = this.category.timeframes.weekly.previous
            this.dateText = "week"
        },
        viewMonthly() {
            this.current = this.category.timeframes.monthly.current
            this.previous = this.category.timeframes.monthly.previous
            this.dateText = "month"
        },
    },
    watch: {
        daily() {
            this.viewDaily()
        },
        weekly() {
            this.viewWeekly()
        },
        monthly() {
            this.viewMonthly()
        }
    },
})
</script>