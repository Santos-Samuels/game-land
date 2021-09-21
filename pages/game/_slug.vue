<template>
    <div>
        {{ game }}
    </div>
</template>

<script>
import axios from 'axios'

export default {
  async asyncData(route) {
    const gameID = route.params.slug
    const api = `https://www.freetogame.com/api/game?id=${gameID}`
    const game = await axios.get(api).then((response) => {
      return response.data
    }) 
    return { game }
  }
}
</script>