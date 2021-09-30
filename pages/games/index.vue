<template>
    <div>
      <div class="mx-5 md:mx-10 lg:mx-20 my-8">
          <section class="border-b border-opacity-25 pb-1 flex justify-between">
              <div class="relative max-w-56">
                <p class="text-gray-500 font-semibold mr-2" v-on:click="toggleSortMenu()">Organizar por: <span class="text-gray-100 ml-3">{{ sortValue == undefined ? 'All' : sortValue }} <i class="ml-2" :class="toggleSort ? 'bi bi-chevron-up' : 'bi bi-chevron-down'"></i></span> </p>
                <div class="absolute z-20 mt-1 right-0">
                  <div class="flex flex-col bg-dracula py-2 rounded" :class="toggleSort ? '' : 'hidden'" v-on:click="toggleSortMenu()">
                    <nuxt-link class="py-1 px-10 hover:bg-blue-500 w-full" tag="a" :to="{ query: {sortTerm: 'all'} }" watchQuery>All</nuxt-link>
                    <nuxt-link class="py-1 px-10 hover:bg-blue-500 w-full" tag="a" :to="{ query: {sortTerm: 'release-date'} }" watchQuery>Release date</nuxt-link>
                    <nuxt-link class="py-1 px-10 hover:bg-blue-500 w-full" tag="a" :to="{ query: {sortTerm: 'alphabetical'} }" watchQuery>Alphabetical</nuxt-link>
                    <nuxt-link class="py-1 px-10 hover:bg-blue-500 w-full" tag="a" :to="{ query: {sortTerm: 'popularity'} }" watchQuery>Popularity</nuxt-link>
                  </div>
                </div>
              </div>

              <div>
                <i class="bi bi-funnel-fill text-2xl"></i>
              </div>
          </section>

          <section class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 mt-4 justify-items-stretch">
              <GameCard v-for="card in cards" :key="card.id" :card="card" />
          </section>
      </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      sortValue: this.$route.query.sortTerm,
      toggleSort: false
    }
  },

  watchQuery: ['sortTerm'],

  async asyncData(route) {
    const sortTerm = route.query.sortTerm
    var options = {
      method: 'GET',
      url: 'https://free-to-play-games-database.p.rapidapi.com/api/games',
      params: {'sort-by': `${sortTerm}`},
      headers: {
        'x-rapidapi-host': 'free-to-play-games-database.p.rapidapi.com',
        'x-rapidapi-key': 'eb4f08aa35msh3746b2d4c081463p10e00ajsn1130b1d401f0'
      }
    };

    const cards = await axios(options).then(function (response) {
      return response.data
    })

    return { cards }
  },
  
  methods: {
    toggleSortMenu() {
      this.toggleSort = !this.toggleSort
    }
  }
}
</script>