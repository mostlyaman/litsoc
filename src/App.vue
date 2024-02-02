
<script>
    import router from './routes';
    export default {
        name: 'App',
        router,
    };
</script>

<template>
    <div id="app">
      <router-view></router-view>
    </div>
</template>

<style>
@import url('https://fonts.googleapis.com/css2?family=Open+Sans:wght@300;400;500;600&family=Poppins:wght@300;400;500;600&display=swap');

* {
    font-family: 'Poppins', sans-serif !important;
}
</style>