<template>
    <nuxt-link tag="a" :to="'/games/' + card.id" class="relative card-container">
        <article class="card-content">
            <img class="rounded-t-md card-thumbnail w-full" :src="card.thumbnail" :alt="card.title" rel="preload" as="image">

            <div class="rounded-b-md bg-gray-800 p-3">
                <p class="text-xl font-bold max-w-prose truncate">{{ card.title }}</p>
                <p class="text-gray-400 truncate">{{ card.developer }}</p>

                <div class="flex justify-between mt-5">
                    <span class="bg-green-500 px-1 rounded">FREE</span>
                    <span class="bg-gray-600 px-1 rounded">{{ card.genre }}</span>
                </div>
            </div>
        </article>

        <div class="card-description absolute top-0 z-10 bg-gray-600 bg-opacity-75 h-full w-full rounded-md p-5">
            <p>{{ card.short_description }}</p>
        </div>
    </nuxt-link>
</template>

<script>
export default {
    props: {
        card: { type: Object, required: true}
    }
}
</script>

<style scoped>
.card-description {
    display: none;
}

.card-container:hover .card-description {
    display: initial;
}

</style>