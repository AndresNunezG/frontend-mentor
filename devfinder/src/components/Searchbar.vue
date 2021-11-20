<template>
    <div class="searchbar bg-primary br-10 b-shadow" :class="{'b-error' : error}">
        <div class="form">
            <div class="form-item">
                <label for="username"><i class="fas fa-search fg-info fs-24"></i></label>
                <input
                 @keypress.enter="emitSearch"
                 v-model="username"
                 class="search-input fs-18 fg-primary"
                 id="username"
                 type="text"
                 placeholder="Search GitHub username..."
                >
            </div>
            <button
             @click="emitSearch"
             type="button"
             class="btn-search br-5 bg-info fg-primary"
            >
            Search
            </button>
        </div>
    </div>
</template>

<script>
export default({
    name: 'Searchbar',
    props: {
        error: Boolean,
    },
    data() {
        return {
            username: '',
        }
    },
    methods: {
        emitSearch() {
            this.$emit('doSearch', this.username)
        }
    },
})
</script>

<style scoped>
.searchbar {
    padding: 0.5em;
    border: 1px solid var(--bg-color-primary);
    transition: 200ms ease;
}
.form {
    display: flex;
    justify-content: space-between;
}
.form-item {
    width: 100%;
    display: flex;
    align-items: center;
    padding-left: 1em;
}
.search-input {
    background: none;
    border: none;
    width: 100%;
    padding-left: 0.5em;
}
.search-input:focus {outline: none;}
.btn-search {
    padding: 0 1em;
    border: none;
    height: 3em;
    color: #fff;
}
.btn-search:active {outline: none;}
.b-error {border: 1px solid rgb(255,51,51);}
</style>