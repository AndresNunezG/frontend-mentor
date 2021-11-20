<template>
    <div class="searchbar bg-primary br-10">
        <form action="" class="form">
            <div class="form-item">
                <label for="username"><i class="fas fa-search fg-info fs-24"></i></label>
                <input  class="search-input fs-18 fg-primary" id="username" type="text" placeholder="Search GitHub username...">
            </div>
            <button class="btn-search br-5 bg-info fg-primary">Search</button>
        </form>
    </div>
</template>

<script>
export default({
    name: 'Searchbar'
})
</script>

<style scoped>
.searchbar {
    padding: 0.5em;
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
.search-input:focus {
    outline: none;
}
.btn-search {
    padding: 0 1em;
    border: none;
    height: 3em;
}
</style>