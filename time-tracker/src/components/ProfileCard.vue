<template>
    <div class="profile-container br">
        <div class="profile-card br">
            <div class="profile-picture-container">
                <img src="../assets/images/image-jeremy.png" alt="profile-picture">
            </div>
            <div class="name-container">
                <p class="fw-300">Report for:</p>
                <div class="name">
                    <h1 class="fw-400">Jeremy&nbsp;</h1>
                    <h1 class="fw-400">Robson</h1>
                </div>
            </div>
        </div>
        <div class="data-filter-container">
            <p class="fg-sec"><button @click="viewDailyAll" class="date-filter btn">Daily</button></p>
            <p class="fg-sec"><button @click="viewWeeklyAll" class="date-filter btn">Weekly</button></p>
            <p class="fg-sec"><button @click="viewMonthlyAll" class="date-filter btn">Monthly</button></p>
        </div>
    </div>
</template>

<script>
export default({
    name: "ProfileCard",
    methods: {
        viewDailyAll() {
            this.$emit("viewdailyall")
        },
        viewWeeklyAll() {
            this.$emit("viewweeklyall")
        },
        viewMonthlyAll() {
            this.$emit("viewmonthlyall")
        },
    }
})
</script>