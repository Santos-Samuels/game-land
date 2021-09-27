<template>
  <div class="">
    <Header />
    <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 mx-20 my-10">
      <GameCard v-for="card in cards" :key="card.id" :card="card" />
    </div>

  </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData() {
    const api = 'https://www.freetogame.com/api/games'
    const cards = await axios.get(api).then((response) => {
      return response.data
    }) 
    return { cards }
  }
}
</script>
