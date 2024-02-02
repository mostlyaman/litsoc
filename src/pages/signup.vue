<script setup>
    import { ref } from 'vue';
    import { useRouter } from 'vue-router';
    import { API } from '../utils/API';
    
    const name = ref('');
    const emailOrPhone = ref('');
    const password = ref('');
    const error = ref(null);
    
    const navigate = useRouter();

    const handleChangeNameOrPhone = (e) => {
        name.value = e.target.value;
    }; 

    const handleChangeEmailOrPhone = (e) => {
        emailOrPhone.value = e.target.value;
    };

    const handleChangePassword = (e) => {
        password.value = e.target.value;
    };

    const signup = async () => {
        try {
            
            if (emailOrPhone.value === '' || password.value === '') {
                error.value = 'Please fill in all fields';
                return;
            }

            console.log(name.value, emailOrPhone.value, password.value)
            
            await API.post(`/user/signUp`, {
                name: name.value,
                emailOrPhone: emailOrPhone.value,
                password: password.value
            });

            navigate.push('/signIn');
        } catch (error) {
            error.value = error.response.data.message;
        }
    };

</script>

<template>
    <div class="flex justify-center items-center h-screen">
        <div 
            class="border-solid rounded-md w-full h-auto min-h-96 m-2 pt-10 pb-10 sm:w-3/4 
            md:w-1/3 lg:w-1/3 xl:w-1/3 p-3 bg-white shadow-xl
            shadow-neutral-300"
        >
            <h1 class="mb-4 text-3xl font-serif text-center">Softral</h1>
            <form>
                <div class="mb-4">
                    <label for="name" class="text-zinc-700 block mb-2 font-medium">Name</label>
                    <input 
                        v-model="name" 
                        type="text" 
                        id="name" 
                        placeholder="Enter your name" 
                        class="w-full px-4 py-2 border border-gray-300
                        rounded focus:outline-none focus:border-blue-500"
                        @input="handleChangeNameOrPhone"
                    >
                </div>
                <div class="mb-4">
                    <label for="emailOrPhone" class="text-zinc-700 block mb-2 font-medium">Email</label>
                    <input 
                        v-model="emailOrPhone" 
                        type="text" 
                        id="emailOrPhone" 
                        placeholder="Enter your email or phone" 
                        class="w-full px-4 py-2 border border-gray-300
                        rounded focus:outline-none focus:border-blue-500"
                        @input="handleChangeEmailOrPhone"
                    >
                </div>
                <div class="mb-4">
                    <label for="password" class="text-zinc-700 block mb-2 font-medium">Password</label>
                    <input 
                        v-model="password" 
                        type="password" 
                        id="password" 
                        placeholder="Enter your password" 
                        class="w-full px-4 py-2 border border-gray-300
                        rounded focus:outline-none focus:border-blue-500"
                        @input="handleChangePassword"
                    >
                </div>
                <button 
                    @click.prevent="signup" 
                    class="w-full px-4 py-2 my-2 text-white
                    bg-zinc-900 rounded hover:bg-blue-600
                    bg-gradient-to-r from-zinc-600 to-zinc-800 transition duration-500"
                >
                    Sign up
                </button>
                <span>{{ error }}</span>
            </form>
            <div class="text-center mt-5">
                <a href="/signIn" class="text-blue-500 hover:underline font-serif text-md">
                    Go to Sign In
                </a>
            </div>
        </div>
    </div>
</template>