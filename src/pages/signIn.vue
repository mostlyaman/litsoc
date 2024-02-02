<script setup>
    import { ref } from 'vue';
    import { useRouter } from 'vue-router';
    import { API } from '../utils/API';


    const emailOrPhone = ref('');
    const password = ref('');
    const error = ref(null);
    const navigate = useRouter();

    const handleChangeEmailOrPhone = (e) => {
        emailOrPhone.value = e.target.value;
    };

    const handleChangePassword = (e) => {
        password.value = e.target.value;
    };

    const signin = async () => {

        try {
            if (emailOrPhone.value === '' || password.value === '') {
                error.value = 'Please fill in all fields';
                return;
            }
            
            await API.post(`/user/signIn`, {
                emailOrPhone: emailOrPhone.value,
                password: password.value
            });

            navigate.push('/dashboard');
        } catch (error) {
            console.log(error.response.data.message)
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
                    <div class="flex flex-row justify-between mt-2 pl-1 pr-1">
                        <label for="remember">
                            <input type="checkbox" name="remember"> Remember me
                        </label>
                        <a href="#" class="text-blue-500 hover:underline">Forgot password?</a>
                    </div>
                </div>
                <button 
                    @click.prevent="signin" 
                    class="w-full px-4 py-2 text-white
                    bg-zinc-900 rounded hover:bg-blue-600
                    bg-gradient-to-r from-zinc-600 to-zinc-800 transition duration-500"
                >
                    Sign In
                </button>
                <span>{{ error }}</span>
            </form>
            <p class="text-zinc-700 mt-4 text-center font-medium">
                Don't have an account? <a href="/signup" class="text-blue-500 hover:underline">Sign up</a>
            </p>
        </div>
    </div>
</template>