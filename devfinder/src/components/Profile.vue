<template>
    <div class="profile-container bg-primary">
        <div class="image-container">
            <img :src="userData.avatar_url" class="profile-image" alt="profile-picture">
        </div>
        <div class="profile-header-container">
            <div class="profile-header-username">
                <h1 class="profile-name">{{ userData.name }}</h1>
                <h2 class="profile-username">@{{ userData.login }}</h2>
                <p class="biography">{{ userData.bio }}</p>
            </div>
            <p class="date-joined">{{ userData.created_at }}</p>
        </div>
        <div class="stats-container">
            <div class="stats-item">
                <p>Repos</p>
                <p>{{ userData.public_repos }}</p>
            </div>
            <div class="stats-item">
                <p>Followers</p>
                <p>{{ userData.followers }}</p>
            </div>
            <div class="stats-item">
                <p>Following</p>
                <p>{{ userData.following }}</p>
            </div>
        </div>
        <div class="extra-info-container">
            <div class="extra-info-item">
                <i class="fas fa-map-marker-alt"></i>
                <span>{{ userData.location }}</span>
            </div>
            <div class="extra-info-item">
                <i class="fab fa-twitter"></i>
                <span>{{ userData.twitter_username }}</span>
            </div>
            <div class="extra-info-item">
                <i class="fas fa-link"></i>
                <a :href="userData.blog">
                    {{ userData.blog }}
                </a>
            </div>
            <div class="extra-info-item">
                <i class="fas fa-building"></i>
                <span>{{ userData.company }}</span>
            </div>
        </div>
    </div>
</template>

<script>
export default({
    name: "Profile",
    props: {
        userData: Object,
    }
})
</script>

<style scoped>
.profile-image {
    border-radius: 50%;
}
.profile-header-container {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
}
.stats-container {
    display: flex;
}
.extra-info-container {
    display: flex;
    flex-wrap: wrap;
}
.extra-info-item {
    width: 50%;
}
</style>