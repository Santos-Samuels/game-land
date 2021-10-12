<template>
    <div class="mx-5 md:mx-10 lg:mx-20 my-8">
        <section class="grid grid-cols-1 md:grid-cols-2 gap-5">
            <div class="flex justify-center">
                <img class="hidden md:w-3/4 md:block" src="@/static/hero.svg" alt="hero">
            </div>
            <div class="text-center bg-dracula px-5 lg:px-10 py-10 rounded-md">
                <nuxt-link tag="a" to="/" class="logo">
                    <p class="font-bold text-3xl md:text-4xl whitespace-nowrap"><i class="bi bi-controller text-3xl md:text-4xl mr-3 text-blue-500"></i>GAME<span class="text-blue-500">LAND</span></p>
                </nuxt-link>
                <h1 class="font-semibold text-2xl mt-3">Log in to continue</h1>

                
                <form class="flex flex-col items-center space-y-4 mt-7">
                    <input class="w-full md:w-3/4 px-3 py-2 rounded-md bg-gray-700" type="text" name="user-name" id="user-name" placeholder="Username" required>
                    <input class="w-full md:w-3/4 px-3 py-2 rounded-md bg-gray-700" type="password" name="user-password" id="user-password" placeholder="Password" required>
                    <button class="w-full md:w-3/4 text-center rounded py-3 bg-gradient-to-b from-blue-400 to-indigo-900 hover:to-indigo-700 transition duration-700 ease-in-out">Login</button>
                </form>

                <div class="mt-7 text-blue-500 ">
                    <a href="#" class="hover:text-gray-100">Forgot Password?</a> <br>
                    <span class="text-gray-500">Not a member yet? </span> <a href="#" class="hover:text-gray-100">Create Account</a>
                </div>
            </div>
        </section>
    </div>
</template>