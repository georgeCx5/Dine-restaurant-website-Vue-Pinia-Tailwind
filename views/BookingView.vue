<script>
import logo from '@/assets/images/logo.svg?url'
import ButtonManager from '../components/ButtonManager.vue';

export default {
   data() {
      return {
         logo,
         bgHeroMB: 'bg-[url(@/assets/images/booking/hero-bg-mobile.jpg)]',
      }
   },
   components: {
      ButtonManager,
   }
}
</script>
<template>
   <header
      :class="` flex flex-col justify-start items-center w-full max-w-[425px] h-[600px] mb-[534px] pt-14 px-6 ${bgHeroMB} bg-cover bg-center text-white text-center`">
      <RouterLink class=" mb-11" to="/">
         <img class=" h-8 " :src="logo" alt="logo">
      </RouterLink>
      <h1 class=" mb-3 text-[2rem] leading-[2.5rem] tracking-[-.025rem] font-light">
         Reservations</h1>
      <p class=" mb-5 text-[1rem] leading-[1.625rem]">
         We can’t wait to host you. If you have any special requirements please feel free to
         call on the phone number below. We’ll be happy to accommodate you.
      </p>
      <ButtonManager btn-type="Dark" btn-text="Reserve place" />
   </header>
</template>