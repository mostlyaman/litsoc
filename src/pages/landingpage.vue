<script>
 import NavBar from '../components/nav/navBar.vue';
 import MobileNav from '../components/mobile/mobileNav.vue';
 import Footer from '../components/footer/footer.vue';

 // Sections
 import SectionIntro from '../components/section/section-1.vue';
 import SectionTwo from '../components/section/section-2.vue';
 import SectionThree from '../components/section/section-3.vue';
 import SectionFour from '../components/section/section-4.vue';
 import SectionFive from '../components/section/section-5.vue';

 export default {
     data() {
         return {
             isMobile: false,
         };
     },
     components: {
         NavBar,
         MobileNav,
         Footer,
         SectionIntro,
         SectionTwo,
         SectionThree,
         SectionFour,
         SectionFive,
     }, 
     methods: {
         getData() {
            return [
                {
                    title: 'TSOD',
                    subtitle: 'Debating Club',
                    img: '/litsoc/clubs/tsod.jpeg'
                },
                {
                    title: 'Qurosity',
                    subtitle: 'Quizzing Club',
                    img: '/litsoc/clubs/quro.png'
                },
                {
                    title: 'UhlLekh',
                    subtitle: 'Writing Club',
                    img: '/litsoc/clubs/uhl.png'
                },
                {
                    title: 'GriffonSight',
                    subtitle: 'Student Media Body',
                    img: '/litsoc/clubs/grif.jpeg'
                },
                
            ];
         },
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
    <img src="/litsoc/bg.png" class="absolute w-full top-0" />
    <div 
        class="flex flex-col bg-white opacity-100
        bg-no-repeat bg-contain bg-top xl:bg-right lg:bg-right h-screen"
    >
        
        <!-- Navigation bar -->
        <NavBar />
        <!-- <MobileNav v-if="isMobile" /> -->

        <main>
            <!-- Section 1 -->
            <SectionIntro />

            <!-- Section 2 -->
            <!-- <SectionTwo /> -->

            <!-- Section 3 -->
            <SectionThree :getData="getData" />
            <!-- Section 4 -->
            <SectionFour />


        </main>
        <!-- <Footer />  -->
    </div>
</template>

<style>
    @keyframes goup {
        0% {
            transform: translateY(0);
        }
        100% {
            transform: translateY(-20px);
        }
        
    }

    .animate-goup {
        animation: goup 1s ease-in-out infinite alternate;
    }
</style>