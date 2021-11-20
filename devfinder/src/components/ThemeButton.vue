<template>
    <div>
        <div v-if="themeActive" class="theme-item">
            <button @click="$emit('changeTheme')" class="btn fg-primary">
                <span>LIGHT&nbsp;</span>
                <i class="fas fa-sun"></i>
            </button>
        </div>
        <div v-else class="theme-item">
            <button @click="$emit('changeTheme')" class="btn fg-primary">
                <span>DARK&nbsp;</span>
                <i class="fas fa-moon"></i>
            </button>
        </div>
    </div>
</template>

<script>
export default ({
    name:'ThemeButton',
    props: {
        themeActive: Boolean,
    }
})
</script>

<style scoped>
.theme-item {
    display: flex;
    align-items: center;
}
.btn {
    letter-spacing: 2px;
    background: none;
    border: none;
    cursor: pointer;
}
</style>