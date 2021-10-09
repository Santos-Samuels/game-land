<template>
  <div class="">
    <div class="bg-gradient-to-r from-blue-400 via-indigo-900 to-blue-600 w-full h-10 transform skew-y-2"></div>
    
    <section class="grid grid-cols-1 md:grid-cols-2 bg-blue-500 bg-opacity-25 px-5 md:px-10 lg:px-20 py-16 transform skew-y-2 mt-6">
      <div>
        <h1 class="text-3xl md:text-5xl font-semibold mb-3">Free Games</h1>
        <h1 class="text-gray-400 font-semibold">We are GameLand, a new gaming platform that brings all the best free multiplayer and MMO games in one place.</h1>
      </div>
    </section>
    
    <section class="mx-5 md:mx-10 lg:mx-20 my-14">
      <h1 class="text-2xl md:text-4xl font-semibold mb-3">Recommendations</h1>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-3">
        <GameCard v-for="card in recommendationsCards" :key="card.id" :card="card" />
      </div>
    </section>
    
    <section class="mx-5 md:mx-10 lg:mx-20 my-14">
      <h1 class="text-2xl md:text-4xl font-semibold mb-3">Trending Games</h1>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-3">
        <TrendingCard v-for="card in trendingCards" :key="card.id" :card="card" />
      </div>
    </section>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
    }
  },

  async asyncData() {
    var options = {
      method: 'GET',
      url: 'https://free-to-play-games-database.p.rapidapi.com/api/games',
      headers: {
        'x-rapidapi-host': 'free-to-play-games-database.p.rapidapi.com',
        'x-rapidapi-key': 'eb4f08aa35msh3746b2d4c081463p10e00ajsn1130b1d401f0'
      }
    };

    const cards = await axios(options).then(function (response) {
      return response.data
    })

    const recommendationsCards = []
    cards.forEach(card => {
      if(card.title == 'Dota 2' || card.title == 'Apex Legends' || card.title == 'Genshin Impact')
        recommendationsCards.push(card)
    });

    const indexList = [57, 286, 212, 24, 226, 452]

    const trendingCards = []
    for(let i=0; i<indexList.length; i++) {
      trendingCards.push(cards.find(card => { return card.id == indexList[i] }))
    }

    return { recommendationsCards, trendingCards }
  }
}
</script>
