<template>
    <div>
        <div class="mx-5 md:mx-10 lg:mx-20 my-8">
          <section>
            <div class="grid grid-cols-1 md:grid-cols-3 relative">
              <div class="md:col-span-2">
                <h1 class="text-xl font-semibold mb-3 -mt-5">{{ game.title }}</h1>
                <div class="hidden md:block">
                  <img class="rounded w-full" :src="game.screenshots[0].image" :alt="game.title">
                  <p class="text-right"><i class="bi bi-info-circle mr-1"></i> Aqui seria um trailer do game</p>
                </div>
              </div>
              
              <div class="md:ml-10 md:mt-5">
                <img class="rounded w-full" :src="game.thumbnail" :alt="game.title">
                <p class="text-xl mt-3">TAGS: <span class="text-base bg-green-500 rounded p-1 ml-2">FREE</span> <nuxt-link tag="a" :to="{ path: '/games', query: { category: game.genre }}" class="text-base border rounded p-1 ml-2 hover:bg-gray-600">{{ game.genre }}</nuxt-link></p>
                <p class="text-xl mt-3">{{ game.short_description }}</p>

                <div class="grid grid-cols-1">
                  <a class="text-center rounded py-3 bg-gradient-to-b from-blue-400 to-indigo-900 hover:to-indigo-700 mt-3 transition duration-700 ease-in-out" :href="game.game_url">GET</a>
                </div>
              </div>
            </div>

            <div class="mt-4 border-t border-b border-opacity-25 grid grid-cols-2 md:grid-cols-3 gap-5 py-5">
              <article>
                <p class="text-sm text-gray-500">TITLE</p>
                <p>{{ game.title }}</p>
              </article>
              <article>
                <p class="text-sm text-gray-500">GENRE</p>
                <p>{{ game.genre }}</p>
              </article>
              <article>
                <p class="text-sm text-gray-500">EDITOR</p>
                <p>{{ game.publisher }}</p>
              </article>
              <article>
                <p class="text-sm text-gray-500">RELEASE DATE</p>
                <p>{{ new Date(game.release_date).getDate() + ' de ' + new Date(game.release_date).toLocaleString('default', { month: 'long' }) + ' de ' + new Date(game.release_date).getFullYear() }}</p>
              </article>
              <article>
                <p class="text-sm text-gray-500">DEVELOPER</p>
                <p>{{ game.developer }}</p>
              </article>
              <article>
                <p class="text-sm text-gray-500">PLATFORM</p>
                <p>{{ game.platform }}</p>
              </article>
            </div>
          </section>

          <section class="mt-5">
            <h1 class="text-xl font-semibold mb-3">{{ game.title }} Screenshots</h1>
            <div class="grid grid-cols-2 md:grid-cols-4 gap-2">
              <img class="rounded cursor-pointer" v-for="screenshot in game.screenshots" :key="screenshot.id" :src="screenshot.image" v-on:click="screenshot_info.image = screenshot.image, screenshot_info.toggle = true">
            </div>
            
            <Screenshot :screenshot_info="screenshot_info" />
          </section>

          <section class="mt-5">
            <p v-if="checked_description" class="text-base mt-3">{{ game.description }}</p>
            <div class="grid grid-cols-1 md:grid-cols-2 my-1 justify-center">
              <button v-on:click="toggleDescription()" class="bg-gray-600 bg-opacity-50 rounded py-1 md:col-start-2 md:col-span-3">GAME DESCRIPTION <i class="ml-1" :class="checked_description ? 'bi bi-chevron-up' : 'bi bi-chevron-down'"></i></button>
            </div>
          </section>

          <section class="mt-5" v-if="game.minimum_system_requirements">
            <h1 class="text-xl font-semibold mb-3">Minimum requirements</h1>

            <div class="bg-dracula p-5 rounded grid grid-cols-2 md:grid-cols-3 gap-5">
              <article>
                <p class="text-sm text-gray-500">Operational System - SO</p>
                <p>{{ game.minimum_system_requirements.os }}</p>
              </article>
              <article>
                <p class="text-sm text-gray-500">Processor</p>
                <p>{{ game.minimum_system_requirements.processor }}</p>
              </article>
              <article>
                <p class="text-sm text-gray-500">Memory</p>
                <p>{{ game.minimum_system_requirements.memory }}</p>
              </article>
              <article>
                <p class="text-sm text-gray-500">Storage</p>
                <p>{{ game.minimum_system_requirements.storage }}</p>
              </article>
              <article>
                <p class="text-sm text-gray-500">Graphics card</p>
                <p>{{ game.minimum_system_requirements.graphics }}</p>
              </article>
            </div>
          </section>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      checked_description: false,
      screenshot_info: { image: '', toggle: false }
    }
  },

  async asyncData(route) {
    const gameID = route.params.slug
    // const api = `https://www.freetogame.com/api/game?id=${gameID}`
    // const game = await axios.get(api).then((response) => {
    //   return response.data
    // }).catch(function (error) {
    //   console.error(error);
    // });
    // return { game }

    var options = {
      method: 'GET',
      url: 'https://free-to-play-games-database.p.rapidapi.com/api/game',
      params: {id: `${gameID}`},
      headers: {
        'x-rapidapi-host': 'free-to-play-games-database.p.rapidapi.com',
        'x-rapidapi-key': 'eb4f08aa35msh3746b2d4c081463p10e00ajsn1130b1d401f0'
      }
    };

    const game = await axios(options).then(function (response) {
      return response.data
    })

    return { game }
  },

  methods: {
    toggleDescription() {
      this.checked_description = !this.checked_description
    }
  }
}
</script>

<style scoped>
</style>