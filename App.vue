<script>
import { RouterLink, RouterView } from 'vue-router'
import logo from '@/assets/images/logo.svg?url'
export default {
  data() {
    return {
      logo,
    }
  }
}
</script>

<template>
  <body class=" flex flex-col items-center bg-white text-neo-ebony-clay font-spartan">
    <RouterView />
    <footer class=" w-full max-w-[425px] bg-neo-cod-gray text-white">
      <div class=" flex flex-col items-center gap-10 py-20">
        <img class=" select-none" :src="logo" alt="logo" draggable="false">
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