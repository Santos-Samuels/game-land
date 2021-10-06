<template>
    <div>
      <div class="mx-5 md:mx-10 lg:mx-20 my-8">
          <section class="border-b border-opacity-25 pb-1 flex justify-between items-end">
              <div class="relative max-w-56">
                <p class="text-gray-500 font-semibold mr-2" v-on:click="toggleSortMenu()">Organizar por: <span class="text-gray-100 ml-3 capitalize">{{ sortValue == undefined ? 'All' : sortValue }} <i class="ml-2" :class="toggleSort ? 'bi bi-chevron-up' : 'bi bi-chevron-down'"></i></span> </p>
                <div class="absolute z-20 mt-1 right-0">
                  <div class="flex flex-col bg-dracula py-2 rounded" :class="toggleSort ? '' : 'hidden'" v-on:click="toggleSortMenu()">
                    <nuxt-link class="py-1 px-10 hover:bg-blue-500 w-full" tag="a" :to="{ query: {platform: this.$route.query.platform, category: this.$route.query.category, sortTerm: 'all'} }" watchQuery>All</nuxt-link>
                    <nuxt-link class="py-1 px-10 hover:bg-blue-500 w-full whitespace-nowrap" tag="a" :to="{ query: {platform: this.$route.query.platform, category: this.$route.query.category, sortTerm: 'release-date'} }" watchQuery>Release date</nuxt-link>
                    <nuxt-link class="py-1 px-10 hover:bg-blue-500 w-full" tag="a" :to="{ query: {platform: this.$route.query.platform, category: this.$route.query.category, sortTerm: 'alphabetical'} }" watchQuery>Alphabetical</nuxt-link>
                    <nuxt-link class="py-1 px-10 hover:bg-blue-500 w-full" tag="a" :to="{ query: {platform: this.$route.query.platform, category: this.$route.query.category, sortTerm: 'popularity'} }" watchQuery>Popularity</nuxt-link>
                  </div>
                </div>
              </div>

              <div>
                <i class="bi bi-funnel-fill text-2xl cursor-pointer hover:text-blue-500 transition duration-300 ease-in-out"></i>
              </div>
          </section>

          <section class="grid grid-cols-4 items-start mt-4">
            <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-3 gap-4 col-span-3">
              <GameCard v-for="card in cards" :key="card.id" :card="card" />
            </div>

            <div class="ml-3">
              <TheFilter />
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
      sortValue: this.$route.query.sortTerm,
      toggleSort: false,
      togglePlatform: false,
      toggleCategory: false
    }
  },

  watchQuery: ['platform', 'category', 'sortTerm'],

  async asyncData(route) {
    const sortTerm = !route.query.sortTerm ? 'alphabetical ' : route.query.sortTerm
    const platformValue = !route.query.platform ? 'all' : route.query.platform
    const categoryValue = route.query.category

    var options = {}
    if(!route.query.category) {
      options = {
        method: 'GET',
        url: 'https://free-to-play-games-database.p.rapidapi.com/api/games',
        params: { platform: `${platformValue}`, 'sort-by': `${sortTerm}` },
        headers: {
          'x-rapidapi-host': 'free-to-play-games-database.p.rapidapi.com',
          'x-rapidapi-key': 'eb4f08aa35msh3746b2d4c081463p10e00ajsn1130b1d401f0'
        }
      };
    }
    else {
      options = {
        method: 'GET',
        url: 'https://free-to-play-games-database.p.rapidapi.com/api/games',
        params: { platform: `${platformValue}`, category: `${categoryValue}`, 'sort-by': `${sortTerm}` },
        headers: {
          'x-rapidapi-host': 'free-to-play-games-database.p.rapidapi.com',
          'x-rapidapi-key': 'eb4f08aa35msh3746b2d4c081463p10e00ajsn1130b1d401f0'
        }
      };
    }

    const cards = await axios(options).then(function (response) {
      return response.data
    })

    return { cards }
  },
  
  methods: {
    toggleSortMenu() {
      this.toggleSort = !this.toggleSort
    }
  },

  // beforeCreate() {
  //   this.$route.query = { platform: 'all', category: 'shooter', sortTerm: 'all' }
  //   console.log(this.$route.query)
  //   //?platform=all&category=shooter&sortTerm=all
  // }
}
</script>