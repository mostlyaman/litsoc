<script setup>
const data = [
    {
        title: 'Gandhigiri',
        img: '/litsoc/events/gan.jpg'
    },
    {
        title: 'Weave the Visuals',
        img: '/litsoc/events/weave.jpg'
    },
    {
        title: 'Voice your thoughts',
        img: '/litsoc/events/vyt.jpeg'
    },
    {
        title: 'Marvel',
        img: '/litsoc/events/Marvel.jpg'
    },
    {
        title: 'World Cup Quiz',
        img: '/litsoc/events/w.jpg'
    }
]

</script>

<template>
    <section class="bg-[#23232a] text-white h-auto min-h-screen overflow-hidden">
        <div class="flex flex-col justify-center items-center p-4 md:p-8">

            <div class="text-center mb-4 md:mb-8">
                <h1 class="text-2xl md:text-4xl font-medium text-yellow-500">Amazing Events</h1>
                <!-- <span class="text-sm md:text-base font-medium">What other people are saying about Workreap ❤</span> -->
            </div>

            <div class="flex flex-col items-center mb-4 md:mb-8">
                <h1 class="text-red-600 text-4xl md:text-7xl font-bold">10+</h1>
                <p class="text-sm md:text-base">and still counting</p>
            </div>

            <div class="relative flex flex-col items-center">
                <div class="flex flex-wrap my-12 text-white">
                    <div v-for="(item, index) in data" :key="index" class="w-full sm:w-1/2 md:w-1/3 lg:w-1/4 px-4 mb-8">
                        <div 
                            class="transition ease-in-out hover:-translate-y-1 hover:scale-110 cursor-pointer duration-300 bg-white rounded-lg py-3"
                        >
                            <img :src="item.img" alt="Image" class="w-full h-auto rounded hover:opacity-25 aspect-video object-contain" />
                        </div>
                        <div class="mt-4 text-xl font-bold text-center">
                            <h3>{{ item.title }}</h3>
                        </div>
                        <div class="text-md text-center">
                            <h3>{{ item.subtitle }}</h3>
                        </div>
                    </div>
                </div>
                <!-- <img src="/img-comments.png" alt="" class="z-10 block object-cover opacity-50 h-full w-full md:w-auto"> -->
                <!-- <div class="absolute -bottom-56 z-40 text-center md:text-left px-4 md:px-8">
                    <img src="/img-comments-spinner.png" alt="" class="spin-slow mb-2">
                </div> -->
                <!-- <div class="flex flex-col items-center z-50">
                    <h1 class="text-red-500 text-4xl md:text-6xl font-bold">Excellent reviews till now</h1>
                    <span class="text-4xl md:text-9xl font-bold text-center">100+</span>
                </div> -->
            </div>
        </div>
    </section>

</template>

<style>
    @keyframes spin-slow {
        from {
            transform: rotate(0deg);
        }
        to {
            transform: rotate(360deg);
        }
    }

    .spin-slow {
    animation: spin-slow 5s linear infinite;
}
</style>