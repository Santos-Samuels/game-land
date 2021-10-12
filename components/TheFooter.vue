<template>
    <div class="px-5 md:px-10 lg:px-20 py-5 bg-gray-900">
        <section class="flex flex-col md:flex-row text-center md:justify-between">
            <nuxt-link tag="a" to="/" class="logo">
                <p class="font-bold text-3xl md:text-4xl whitespace-nowrap"><i class="bi bi-controller text-3xl md:text-4xl mr-3 text-blue-500"></i>GAME<span class="text-blue-500">LAND</span></p>
            </nuxt-link>

            <div class="space-x-3 mt-3 md:mt-0">
                <i class="bi bi-facebook text-2xl hover:text-blue-500 transition duration-500 ease-in-ou cursor-pointert"></i>
                <i class="bi bi-twitter text-2xl hover:text-blue-500 transition duration-500 ease-in-out cursor-pointer"></i>
                <i class="bi bi-instagram text-2xl hover:text-blue-500 transition duration-500 ease-in-out cursor-pointer"></i>
                <i class="bi bi-youtube text-2xl hover:text-blue-500 transition duration-500 ease-in-out cursor-pointer"></i>
            </div>
        </section>

        <section class="text-center mt-3">
            <p class="text-gray-500">Developer by <a href="https://github.com/Santos-Samuels" class="text-blue-500 hover:text-gray-100">Samuel Santos</a></p>
        </section>
    </div>
</template>