<script>
import ButtonManagerVue from '../components/ButtonManager.vue';
import FirstFeatures from '../components/FirstFeatures.vue';
import SecondFeatures from '../components/SecondFeatures.vue';

import logo from '@/assets/images/logo.svg?url'
import ptDivide from '@/assets/images/patterns/pattern-divide.svg?url'

export default {
  data() {
    return {
      logo,
      ptDivide,
      bgHeroMB: 'bg-[url(@/assets/images/homepage/hero-bg-mobile@2x.jpg)]',
    }
  },
  components: {
    ButtonManagerVue,
    FirstFeatures,
    SecondFeatures,
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
    <section class=" relative flex flex-col gap-[6.25rem] mt-[-4.5rem] mb-[6.25rem] px-6 z-10">
      <FirstFeatures :data-index="0" />
      <FirstFeatures :data-index="1" />
    </section>
    <section class=" flex flex-col gap-[5.25rem] px-6 pt-[4.5rem] pb-[3rem] bg-neo-cod-gray text-white">
      <article class=" flex flex-col items-center text-center">
        <img class=" mb-9" :src="ptDivide" alt="pattern divide">
        <h2 class=" mb-3 text-[2rem] leading-[2.5rem] tracking-[-0.025rem] font-bold">
          A few highlights from our menu</h2>
        <p class=" text-[1rem] leading-[1.625rem]">
          We cater for all dietary requirements, but here’s a glimpse at some of our diner’s favourites.
          Our menu is revamped every season.
        </p>
      </article>
      <div class=" flex flex-col gap-6">
        <SecondFeatures :data-index="0" />
        <SecondFeatures :data-index="1" />
        <SecondFeatures :data-index="2" />
      </div>
    </section>
  </main>
</template>
