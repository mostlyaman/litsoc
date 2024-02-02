<script>
    export default {
        props: ['getData']
    }
</script>

<template>
        <section 
            class="flex flex-col bg-[#23232a] h-auto pt-20"
        >
            <!-- header -->
            <div class="relative flex flex-col items-center">
                <!-- <h1 class="text-7xl text-red-600 font-bold">4 Amazing</h1> -->
                <h1 class="text-4xl text-yellow-500 font-bold">4 Amazing Clubs</h1>
                <!-- <span class="text-lg text-white font-medium"></span> -->
                <span class="border-b-4 rounded-xl border-red-600 w-20 text-center mt-8"></span>
            </div>

            <!-- nav switching -->
            <div class="flex flex-col justify-between items-center">
                
                <!-- <ul class="flex flex-col items-center gap-14 mt-10 md:flex-row">
                    <li class="">
                        <span 
                            class="border-0 border-b-red-600 hover:border-b-2 pb-3 
                            text-white cursor-pointer border-b-0 hover:transition ease-in-out
                            delay-150"
                        >
                            ALL
                        </span>
                    </li>
                    <li class="">
                        <span 
                            class="border-0 border-b-red-600 hover:border-b-2 pb-3 
                            text-white cursor-pointer border-b-0 hover:transition ease-in-out
                            delay-150"
                        >
                            HOMEPAGE
                        </span>
                    </li>
                    <li class="">
                        <span 
                            class="border-0 border-b-red-600 hover:border-b-2 pb-3 
                            text-white cursor-pointer border-b-0 hover:transition ease-in-out
                            delay-150"
                        >
                            LISTING PAGES
                        </span>
                    </li>
                    <li class="">
                        <span 
                            class="border-0 border-b-red-600 hover:border-b-2 pb-3 
                            text-white cursor-pointer border-b-0 hover:transition ease-in-out
                            delay-150"
                        >
                            DETAIL PAGES
                        </span>
                    </li>
                    <li class="">
                        <span 
                            class="border-0 border-b-red-600 hover:border-b-2 pb-3 
                            text-white cursor-pointer border-b-0 hover:transition ease-in-out
                            delay-150"
                        >
                            OTHERS
                        </span>
                    </li>
                </ul> -->

                <div class="flex flex-wrap my-12 text-white">
                    <div v-for="(item, index) in getData()" :key="index" class="w-full sm:w-1/2 md:w-1/3 lg:w-1/4 px-4 mb-8">
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
            </div>
        </section>
</template>