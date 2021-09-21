<template>
    <div class="m-5">
        <!-- <section class="mt-2">
          <div class="flex justify-between p-2 border-b border-gray-400 border-opacity-25">
            <p class="text-gray-400">Desenvolvedor</p>
            <p class="text-gray-100">{{ game.developer }}</p>
          </div>
          <div class="flex justify-between p-2 border-b border-gray-400 border-opacity-25">
            <p class="text-gray-400">Editora</p>
            <p class="text-gray-100">{{ game.publisher }}</p>
          </div>
          <div class="flex justify-between p-2 border-b border-gray-400 border-opacity-25">
            <p class="text-gray-400">Editora</p>
            <p class="text-gray-100">{{ game.release_date }}</p>
          </div>
          <div class="flex justify-between p-2 border-b border-gray-400 border-opacity-25">
            <p class="text-gray-400">Plataforma</p>
            <p class="text-gray-100">{{ game.platform }}</p>
          </div>
        </section> -->
        <section>
          <div>
            <h1 class="text-xl font-semibold mb-3">{{ game.title }}</h1>
            <img class="rounded w-full" :src="game.thumbnail" :alt="game.title">
            
            <div>
              <p class="text-xl mt-3">{{ game.short_description }}</p>
              <p v-if="checked_description" class="text-base mt-3">{{ game.description }}</p>
              <div class="grid grid-cols-1 my-1">
                <button v-on:click="toggleDescription()" class="bg-gray-600 bg-opacity-50 rounded py-1">SHOW MORE <i class="ml-1" :class="checked_description ? 'bi bi-chevron-up' : 'bi bi-chevron-down'"></i></button>
              </div>
            </div>

            <div class="grid grid-cols-1">
              <a class="text-center rounded py-3 bg-gradient-to-b from-blue-400 to-indigo-900 hover:to-indigo-700 mt-3 transition duration-700 ease-in-out" :href="game.game_url">GET</a>
            </div>
          </div>

          <div class="mt-4 border-t border-b border-opacity-25 grid grid-cols-2 gap-5 py-5">
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
              <p>{{ game.release_date }}</p>
            </article>
            <article>
              <p class="text-sm text-gray-500">DEVELOPER</p>
              <p>{{ game.developer }}</p>
            </article>
            <article>
              <p class="text-sm text-gray-500">PLATFORM</p>
              <p>{{ game.platform }}</p>
            </article>
            <article>
              <p class="text-sm text-gray-500">PRICE</p>
              <p> Free </p>
            </article>
          </div>
        </section>

        <section class="mt-5">
          <h1 class="text-xl font-semibold mb-3">Minimum requirements</h1>

          <div class="game-requirements p-5 rounded grid grid-cols-2 gap-5">
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

        <section>
          <img v-for="screenshot in game.screenshots" :key="screenshot.id" :src="screenshot.image" alt="">
        </section>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      checked_description: false
    }
  },

  async asyncData(route) {
    const gameID = route.params.slug
    const api = `https://www.freetogame.com/api/game?id=${gameID}`
    const game = await axios.get(api).then((response) => {
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
.game-requirements {
  background-color: #202020;
}
</style>