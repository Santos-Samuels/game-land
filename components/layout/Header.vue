<template>
    <div class="px-20 py-3 bg-gray-800 border-b border-gray-500 flex items-center justify-between">
        <div class=" flex items-center space-x-10">
            <div class="logo">
                <p class="font-bold text-4xl"><i class="bi bi-controller text-4xl mr-3 text-blue-600"></i>GAME<span class="text-blue-600">LAND</span></p>
            </div>

            <div class="text-gray-500 font-semibold space-x-2">
                <nuxt-link class="hover:text-gray-100" tag="a" to="#">All Games</nuxt-link>
                <nuxt-link class="hover:text-gray-100" tag="a" to="#">PC</nuxt-link>
                <nuxt-link class="hover:text-gray-100" tag="a" to="#">Browser</nuxt-link>
                <nuxt-link class="hover:text-gray-100" tag="a" to="#">Top 2021</nuxt-link>
            </div>
        </div>

        <div class="text-gray-500 text-xl space-x-2">
            <nuxt-link tag="a" to="#" class="bi bi-search hover:text-gray-100" title="Search for games"></nuxt-link>
            <i class="bi bi-globe hover:text-gray-100 cursor-pointer"></i>
        </div>
    </div>
</template>