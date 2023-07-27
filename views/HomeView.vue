<script>
import logo from '@/assets/images/logo.svg?url'
import ButtonManagerVue from '../components/ButtonManager.vue';
import FirstFeatures from '../components/FirstFeatures.vue';

export default {
  data() {
    return {
      logo,
      bgHeroMB: 'bg-[url(@/assets/images/homepage/hero-bg-mobile@2x.jpg)]',
    }
  },
  components: {
    ButtonManagerVue,
    FirstFeatures,
  }
}
</script>
<template>
  <header
    :class="` flex flex-col justify-center items-center w-full h-[748px] max-w-[425px] pt-20 px-6 ${bgHeroMB} bg-cover bg-center text-white text-center`">
    <img class=" h-8 mb-9" :src="logo" alt="logo">
    <h1 class=" mb-5 px-8 text-[2rem] leading-[2.5rem] tracking-[-.025rem] font-light">
      Exquisite dining since 1989</h1>
    <p class=" mb-[3.25rem] text-[1rem] leading-[1.625rem]">
      Experience our seasonal menu in beautiful country surroundings. Eat the freshest produce from
      the comfort of our farmhouse.
    </p>
    <RouterLink to="/booking">
      <ButtonManagerVue btn-type="Dark" btn-text="Book a table" />
    </RouterLink>
  </header>
  <main class=" w-full max-w-[425px]">
    <section class=" flex flex-col gap-[6.25rem] mt-[-4.5rem] mb-[6.25rem] px-6">
      <FirstFeatures :data-index="0" />
      <FirstFeatures :data-index="1" />
    </section>
  </main>
</template>
