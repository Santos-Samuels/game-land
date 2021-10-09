<template>
    <nuxt-link tag="a" :to="'/games/' + card.id" class="relative card-container transform hover:scale-105 duration-500 ease-in-out shadow-lg">
        <article class="card-content grid grid-cols-5">
            <img class="rounded-l-md card-thumbnail w-full h-full col-span-2" :src="card.thumbnail" :alt="card.title" rel="preload" as="image">

            <div class="rounded-r-md bg-gray-800 p-3 col-span-3">
                <p class="text-xl font-bold max-w-prose truncate">{{ card.title }}</p>
                <p class="text-gray-400 truncate" :title="card.short_description">{{ card.short_description }}</p>

                <div class="flex justify-between mt-5">
                    <span class="bg-green-500 px-1 rounded">FREE</span>
                    <span class="bg-gray-600 px-1 rounded">{{ card.genre }}</span>
                </div>
            </div>
        </article>
    </nuxt-link>
</template>

<script>
export default {
    props: {
        card: { type: Object, required: true}
    }
}
</script>