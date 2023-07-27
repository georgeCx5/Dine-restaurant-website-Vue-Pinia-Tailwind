<script>
import { useMainStore } from '@/stores/MainStore'
import { mapStores } from 'pinia'
import ButtonManager from './ButtonManager.vue'
export default {
   data() {
      return {
         data: [
            {
               header: 'Family Gathering',
               main: 'We love catering for entire families. So please bring everyone along for a special meal with your loved ones. We’ll provide a memorable experience for all.',
               bg: [
                  'bg-[url(@/assets/images/homepage/family-gathering-mobile@2x.jpg)]'
               ]
            },
            {
               header: 'Special Events',
               main: 'Whether it’s a romantic dinner or special date you’re celebrating with others we’ll look after you. We’ll be sure to mark your special date with an unforgettable meal.',
               bg: [
                  'bg-[url(@/assets/images/homepage/special-events-mobile@2x.jpg)]'
               ]
            },
            {
               header: 'Social Events',
               main: 'Are you looking to have a larger social event? No problem! We’re more than happy to cater for big parties. We’ll work with you to make your event a hit with everyone.',
               bg: [
                  'bg-[url(@/assets/images/homepage/social-events-mobile@2x.jpg)]'
               ]
            }
         ]
      }
   },
   components: {
      ButtonManager,
   },
   computed: {
      ...mapStores(useMainStore)
   },
   methods: {
      setActiveButton(value) {
         return value == this.mainStore.featureIndex ? '' : 'text-opacity-50'
      },
   }
}
</script>
<template>
   <div class=" relative h-[400px]">
      <div v-for="(item, index) in data">
         <Transition>
            <div v-show="index == mainStore.featureIndex"
               :class="` absolute w-full h-full ${item.bg} bg-cover bg-center shadow-2xl`"></div>
         </Transition>
      </div>
   </div>
   <div class=" flex flex-col gap-7">
      <div class=" flex flex-col items-center gap-4">
         <div v-for="(item, index) in data" @click="mainStore.featureIndex = index"
            class=" relative flex flex-col items-center z-10">
            <button
               :class="` text-neo-btn ${setActiveButton(index)} hover:text-opacity-100 text-[1rem] leading-[1.75rem] tracking-[.15rem] font-semibold uppercase select-none`">
               {{ item.header }}
            </button>
            <div v-show="index == mainStore.featureIndex" class=" w-12 h-px bg-neo-beaver"></div>
         </div>
      </div>
      <div class=" flex flex-col items-center text-center">
         <h1 class=" mb-3 text-[2rem] leading-[2.5rem] tracking-[-.025rem] font-bold">
            {{ data[mainStore.featureIndex].header }}</h1>
         <p class=" mb-7 text-[1rem] leading-[1.625rem]">
            {{ data[mainStore.featureIndex].main }}
         </p>
         <RouterLink to="/booking">
            <ButtonManager btn-type="Light" btn-text="Book a table" />
         </RouterLink>
      </div>
   </div>
</template>
<style>
.v-enter-active,
.v-leave-active {
   transition: opacity .5s ease;
}

.v-enter-from,
.v-leave-to {
   opacity: 0;
}
</style>