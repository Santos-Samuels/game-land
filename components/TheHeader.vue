<template>
    <header class="px-5 md:px-10 lg:px-20 py-3 bg-gray-900 sticky z-40 top-0 w-full shadow-lg">
        <section class="flex items-center justify-between">
            <div class=" flex items-center md:space-x-10">
                <nuxt-link tag="a" to="/" class="logo">
                    <p class="font-bold text-3xl md:text-4xl whitespace-nowrap"><i class="bi bi-controller text-3xl md:text-4xl mr-3 text-blue-500"></i>GAME<span class="text-blue-500">LAND</span></p>
                </nuxt-link>

                <nav class="text-gray-500 font-semibold absolute md:static top-14 bg-gray-900 py-7 md:py-0 w-full -mx-5 px-10 md:px-0 md:block" :class="!toggle ? 'hidden' : null" v-on:click="toggleMenu()">
                    <div class="flex flex-col md:block text-xl md:text-base space-y-2 md:space-y-0 md:space-x-2">
                        <nuxt-link class="hover:text-gray-100" tag="a" :to="{ name: 'games' }">All Games</nuxt-link>
                        <nuxt-link class="hover:text-gray-100" tag="a" :to="{ name: 'games', query: { platform: 'pc' } }">PC</nuxt-link>
                        <nuxt-link class="hover:text-gray-100" tag="a" :to="{ name: 'games', query: { platform: 'browser' } }">Browser</nuxt-link>
                    </div>
                </nav>
            </div>

            <div class="text-gray-500 space-x-2 hidden md:block">
                <nuxt-link tag="a" to="/games" class="bi bi-search hover:text-gray-100 text-xl" title="Search for games"></nuxt-link>
                <nuxt-link tag="a" to="/login" class="bi bi-person-fill hover:text-gray-100 cursor-pointer text-2xl" title="Login"></nuxt-link>
            </div>

            <div class="block md:hidden">
                <input type="checkbox" name="toggle-menu" id="toggle-menu" class="hidden">
                <label  v-on:click="toggleMenu()" class="transform first:rotate-45" id="toggle-button" for="toggle-menu"><i class="bi bi-list text-3xl cursor-pointer block md:hidden"></i></label>
            </div>
        </section>
    </header>
</template>

<script>
export default {
    data() {
        return {
            toggle: false
        }
    },

    methods: {
        toggleMenu() {
            if(screen.width < 768)
                this.toggle = !this.toggle
        }
    }
}
</script>