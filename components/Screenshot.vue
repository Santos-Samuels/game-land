<template>
    <div v-show="screenshot_info.toggle" v-on:click="screenshot_info.toggle = false">
        <i class="bi bi-x text-5xl fixed top-0 right-0 z-10 m-3"></i>
        <img class="bg-black bg-opacity-75 fixed h-full w-full object-contain top-0 left-0 p-5 md:p-10 lg:p-15" :src="screenshot_info.image" alt="">
    </div>
</template>

<script>
export default {
    props: {
        screenshot_info : { type: Object }
    }
}
</script>