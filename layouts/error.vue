<template>
    <div class="mx-5 md:mx-10 lg:mx-20 my-8 flex flex-col items-center justify-center">
        <div v-if="error.statusCode === 404">
            <img class="w-1/5" src="@/static/error.gif" alt="">
            <h1 class="text-4xl">Opps! Page not found</h1>
            <p class="mt-2 text-xl">Sorry, the page you're looking for doesn't exist.</p>
        </div>
        
        <div>

        </div>

        <nuxt-link class="text-center rounded py-3 w-1/4 bg-gradient-to-b from-blue-400 to-indigo-900 hover:to-indigo-700 mt-5 transition duration-700 ease-in-out" tag="a" to="/">Back to Home</nuxt-link>
    </div>
</template>

<script>
  export default {
    props: ['error'],
    layout: 'error' // you can set a custom layout for the error page
  }
</script>