<template>
    <div class="absolute md:static top-0 bg-black md:bg-transparent bg-opacity-75 h-full rounded-md">
        <div class="bg-dracula w-full rounded-md p-3 border border-gray-700 md:border-none">
            <h1 class="text-blue-500"><i class="bi bi-funnel-fill text-2xl cursor-pointer mr-1"></i><span class="font-semibold text-2xl">Filter</span></h1>

            <section class="flex flex-col mt-4">
                <p class="font-semibold border-b border-opacity-25 text-gray-500 mb-2">Title</p>
                <div action="" class="flex">
                    <input class="appearance-none rounded px-2 py-1 bg-gray-700 md:w-full" v-model="searchTitle" type="text" name="gameTitle" id="gameTitle" placeholder="Enter a game title">
                    <nuxt-link tag="a" :to="{ query: { searchTerm: searchTitle} }" class="ml-1 bg-blue-500 hover:bg-blue-400 px-2 py-1 rounded"><i class="bi bi-search"></i></nuxt-link>
                </div>
            </section>

            <section class="flex flex-col mt-4 space-y-1">
                <p class="font-semibold border-b border-opacity-25 text-gray-500">Platform</p>
                <nuxt-link class="py-1 px-3 hover:bg-blue-500 rounded w-full" :class="this.$route.query.platform == 'all' ? 'active-filter' : ''" tag="a" :to="{ query: {platform: 'all', category: this.$route.query.category, sortTerm: this.$route.query.sortTerm} }" watchQuery> All </nuxt-link>
                <nuxt-link class="py-1 px-3 hover:bg-blue-500 rounded w-full" :class="this.$route.query.platform == 'browser' ? 'active-filter' : ''" tag="a" :to="{ query: {platform: 'browser', category: this.$route.query.category, sortTerm: this.$route.query.sortTerm} }" watchQuery> Browser </nuxt-link>
                <nuxt-link class="py-1 px-3 hover:bg-blue-500 rounded w-full" :class="this.$route.query.platform == 'pc' ? 'active-filter' : ''" tag="a" :to="{ query: {platform: 'pc', category: this.$route.query.category, sortTerm: this.$route.query.sortTerm} }" watchQuery>PC</nuxt-link>
            </section>

            <section class="flex flex-col mt-4">
                <p class="font-semibold border-b border-opacity-25 text-gray-500 mb-1">Category</p>
                <div class="">
                    <nuxt-link v-for="tag in categoryList" :key="tag.index" :class="$route.query.category == tag ? 'active-filter' : ''" class="bg-gray-400 bg-opacity-25 hover:bg-blue-500 px-1 rounded uppercase mr-1" tag="a" :to="{ query: {platform: $route.query.platform, category: tag, sortTerm: $route.query.sortTerm} }" watchQuery> {{ tag }} </nuxt-link>
                </div>
            </section>

            <section class="flex flex-col mt-4">
                <p class="font-semibold border-b border-opacity-25 text-gray-500 mb-1">Utility</p>
                <nuxt-link class="py-1 px-3 hover:bg-blue-500 rounded w-full" tag="a" to="/games" watchQuery>Clear</nuxt-link>
            </section>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            categoryList: ['mmorpg', 'shooter', 'strategy', 'moba', 'racing', 'sports', 'social', 'sandbox', 'open-world', 'survival', 'pvp', 'pve', 'pixel', 'voxel', 'zombie', 'turn-based', 'first-person', 'third-Person', 'top-down', 'tank', 'space', 'sailing', 'side-scroller', 'superhero', 'permadeath', 'card', 'battle-royale', 'mmo', 'mmofps', 'mmotps', '3d', '2d', 'anime', 'fantasy', 'sci-fi', 'fighting', 'action-rpg', 'action', 'military', 'martial-arts', 'flight', 'low-spec', 'tower-defense', 'horror', 'mmorts'],
            searchTitle: ''
        }
    }
}
</script>

<style scoped>
.active-filter {
    background: #3b82f6 !important;
}
</style>