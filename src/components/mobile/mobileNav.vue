
<script>
    export default {
        data() {
            return {
                isDropdownOpen: false,
            };
        },
        methods: {
            toggleDropdown() {
                this.isDropdownOpen = !this.isDropdownOpen;
            },
        },
    };
</script>
<template>
    <div 
        class="flex flex-row justify-between items-center h-11 w-full pl-5 pr-5 z-10"
    >

        <a href="/">
            <img src="/litsoc/logo.png" alt="" class="w-10">
        </a>
        
        <div class="relative">
            <button
                @click="toggleDropdown"
                class="bg-purple-600 text-white w-32 h-auto p-1 rounded-md hover:bg-purple-500 transition ease-in-out duration-300"
            >
                <h2 class="text-center text-lg font-medium">Menu</h2>
            </button>
        
            <ul
                v-show="isDropdownOpen"
                class="absolute bg-white text-black w-[100%] p-2 rounded-md shadow gap-2 top-11"
            >
                <li class="text-xl font-medium hover:bg-slate-500 cursor-pointer hover:text-white transition duration-300">Home</li>
                <li class="text-xl font-medium hover:bg-slate-500 cursor-pointer hover:text-white transition duration-300">Jobs</li>
                <li class="text-xl font-medium hover:bg-slate-500 cursor-pointer hover:text-white transition duration-300">Proposals</li>
                <li
                    class="text-xl font-medium hover:bg-slate-500 cursor-pointer hover:text-white transition duration-300"
                >
                    <a
                        href="/signin"
                    >
                        Sign in
                    </a>
                </li>
                <li
                    class="text-xl font-medium hover:bg-slate-500 cursor-pointer hover:text-white transition duration-300"
                >
                    <a 
                        href="/profile"
                    >
                        Profile
                    </a>
                </li>
            </ul>
        </div>
    </div>
</template>