<template>
    <div class="profile-container bg-primary br-10 b-shadow">
        <div class="left-section">
            <div class="image-container">
                <img :src="userData.avatar_url" class="profile-image" alt="profile-picture">
            </div>
        </div>
        <div class="right-section">
            <div class="profile-header-container">
                <div class="profile-header-username">
                    <h1 v-if="userData.name" class="profile-name fs-24">{{ userData.name }}</h1>
                    <h1 v-else class="profile-name fs-24">Username not available</h1>
                    <h2 class="profile-username fg-info fs-16">@{{ userData.login }}</h2>
                    <p v-if="userData.bio" class="biography fg-secondary fs-16">{{ userData.bio }}</p>
                    <p v-else class="fg-secondary fs-16">This profile has no bio</p>
                </div>
                <p class="date-joined fg-secondary">
                    Joined
                    {{ new Date(userData.created_at).toLocaleDateString("en-GB", dateOptions) }}
                </p>
            </div>
            <div class="stats-container bg-secondary br-10">
                <div class="stats-item">
                    <p class="fg-secondary">Repos</p>
                    <p class="fw-500 fs-18">{{ userData.public_repos }}</p>
                </div>
                <div class="stats-item">
                    <p class="fg-secondary">Followers</p>
                    <p class="fw-500 fs-18">{{ userData.followers }}</p>
                </div>
                <div class="stats-item">
                    <p class="fg-secondary">Following</p>
                    <p class="fw-500 fs-18">{{ userData.following }}</p>
                </div>
            </div>
            <div class="extra-info-container">
                <div class="extra-info-item">
                    <i class="fas fa-map-marker-alt" :class="{'fg-secondary' : !userData.location}"></i>
                    <span v-if="userData.location" class="fs-16">{{ userData.location }}</span>
                    <span v-else class="fg-secondary">Not available</span>
                </div>
                <div class="extra-info-item">
                    <i class="fab fa-twitter" :class="{'fg-secondary' : !userData.twitter_username}"></i>
                    <span v-if="userData.twitter_username" class="fs-16">@{{ userData.twitter_username }}</span>
                    <span v-else class="fg-secondary">Not available</span>
                </div>
                <div class="extra-info-item">
                    <i class="fas fa-link" :class="{'fg-secondary' : !userData.blog}"></i>
                    <a v-if="userData.blog" :href="userData.blog" target="_blank" rel="noopener" class="fg-primary fs-16">
                        {{ userData.blog }}
                    </a>
                    <span v-else class="fg-secondary">Not available</span>
                </div>
                <div class="extra-info-item">
                    <i class="fas fa-building" :class="{'fg-secondary' : !userData.company}"></i>
                    <span v-if="userData.company">{{ userData.company }}</span>
                    <span v-else class="fg-secondary">Not available</span>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default({
    name: "Profile",
    props: {
        userData: Object,
    },
    data() {
        return {
            dateOptions: {
                year: 'numeric',
                month: 'short',
                day: 'numeric'
            },
        }
    }
})
</script>

<style scoped>
.profile-container {
    display: flex;
    padding: 3em 3em 3em 0;
}
.left-section {width: 25%;}
.right-section {width: 75%;}
.image-container {
    display: flex;
    justify-content: center;
    align-items: flex-end;
}
.profile-image {
    border-radius: 50%;
    width: 75%;
}
.profile-header-container {
    display: flex;
    justify-content: space-between;
    align-items: flex-start;
}
.profile-header-username {width: 70%;}
.profile-header-username p {margin-top: 2em;}
.profile-header-username h2 {margin-top: 1em;}
.stats-container {
    display: flex;
    justify-content: space-between;
    padding: 1em 2em;
    margin-top: 2em;
}
.extra-info-container {
    margin-top: 2em;
    display: flex;
    flex-wrap: wrap;
}
.extra-info-item {
    width: 50%;
    display: flex;
    align-items: center;
    overflow-x: scroll;
    margin-bottom: 0.8em;
}
.extra-info-item i {margin: 0 0.7em 0 0.5em}
.extra-info-item a {text-decoration: none;}
</style>