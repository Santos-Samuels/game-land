<template>
  <div class="">
    <Header />
    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 mx-5 md:mx-10 lg:mx-20 my-10">
      <GameCard v-for="card in cards" :key="card.id" :card="card" />
    </div>

  </div>
</template>

<script>
import axios from 'axios'

export default {
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

    return { cards }
  }
}
</script>
