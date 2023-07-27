<script>
import { RouterLink, RouterView } from 'vue-router'
import ButtonManager from './components/ButtonManager.vue';
import logo from '@/assets/images/logo.svg?url'
export default {
  data() {
    return {
      bgFooterMB: 'bg-[url(@/assets/images/homepage/ready-bg-mobile.jpg)]',
      logo,
    }
  },
  components: {
    ButtonManager,
  }
}
</script>

<template>
  <body class=" flex flex-col items-center bg-white text-neo-ebony-clay font-spartan">
    <!-- <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/about">About</RouterLink> -->
    <RouterView />
    <footer class=" w-full max-w-[425px] bg-neo-cod-gray text-white">
      <div :class="` flex flex-col justify-center items-center gap-5 w-full h-[328px] ${bgFooterMB} bg-cover bg-center`">
        <h2 class=" text-center text-[2rem] leading-[2.5rem] tracking-[-.025rem] font-bold">
          Ready to make a reservation?</h2>
        <ButtonManager btn-type="Dark" btn-text="Book a table" />
      </div>
      <div class=" flex flex-col items-center gap-10 py-20">
        <img :src="logo" alt="logo">
        <div class=" flex flex-col gap-8 text-center text-[.875rem] leading-[1.75rem] tracking-[.125rem]">
          <div>
            <p>Marthwaite, Sedbergh</p>
            <p>Cumbria</p>
            <p>+00 44 123 4567</p>
          </div>
          <div>
            <p>Open Times</p>
            <p>Mon - Fri: 09:00 AM - 10:00 PM</p>
            <p>Sat - Sun: 09:00 AM - 11:30 PM</p>
          </div>
        </div>
      </div>
    </footer>
  </body>
</template>