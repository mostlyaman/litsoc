<script>
    import MobileNav from '../components/mobile/mobileNav.vue';
    import NavBar from '../components/nav/navBar.vue';
    import SideBar from '../components/sidebar/sidebar.vue';

    export default {
        data() {
            return {
                isMobile: false,
            }
        },
        components: {
            MobileNav,
            NavBar,
            SideBar,
        },
        methods: {
            checkScreenSize() {
                this.isMobile = window.innerWidth <= 1024;
            }
        },
        mounted() {
            window.addEventListener('resize', this.checkScreenSize);
            this.checkScreenSize();
        },
        beforeDestroy() {
            window.removeEventListener('resize', this.checkScreenSize);
        },
    }
</script>

<template>
    <div>
        <NavBar v-if="!isMobile"/>
        <MobileNav v-if="isMobile" />
        <div class="flex flex-row">
            <SideBar />
            <div class="bg-slate-200 h-screen w-full"></div>
        </div>
    </div>
</template>