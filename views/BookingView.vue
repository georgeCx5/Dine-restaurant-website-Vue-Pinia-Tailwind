<script>
import { useMainStore } from '@/stores/MainStore';
import { mapStores } from 'pinia';

import logo from '@/assets/images/logo.svg?url'
import iconMinus from '@/assets/images/icons/icon-minus.svg?url'
import iconPlus from '@/assets/images/icons/icon-plus.svg?url'
import ButtonManager from '../components/ButtonManager.vue';
import DropdownTime from '../components/DropdownTime.vue';

export default {
   data() {
      return {
         logo,
         iconMinus,
         iconPlus,
         bgHeroMB: 'bg-[url(@/assets/images/booking/hero-bg-mobile.jpg)]',
      }
   },
   components: {
      ButtonManager,
      DropdownTime,
   },
   computed: {
      ...mapStores(useMainStore),
   }
}
</script>
<template>
   <header
      :class="` flex flex-col justify-start items-center w-full max-w-[425px] h-[600px] mb-[534px] px-6 ${bgHeroMB} bg-cover bg-center text-white text-center`">
      <!-- Form -->
      <Transition name="fade">
         <div v-if="!mainStore.isSubmitted" class=" relative top-0 w-full max-w-[425px]">
            <div
               class=" absolute top-[463px] w-full px-8 py-8 bg-white text-neo-inactive text-[1.25rem] leading-[1.75rem] shadow-xl select-none">
               <!-- Name -->
               <div class=" relative flex flex-col gap-3 mb-[2.125rem]">
                  <input @blur="mainStore.checkName()" @keydown="mainStore.isRightName = true"
                     :class="` px-4 placeholder:text-neo-inactive ${mainStore.checkValue(mainStore.isRightName).txtColor} focus:outline-none`"
                     type="text" placeholder="Name" v-model="mainStore.nameVal">
                  <div :class="` w-full h-px ${mainStore.checkValue(mainStore.isRightName).bgColor}`"></div>
                  <h5 v-show="mainStore.isRightName == false"
                     class=" absolute bottom-[-20px] px-4 text-neo-error text-[.625rem] leading-[.625rem] tracking-[-.0075rem]">
                     This field is required</h5>
               </div>
               <!-- Email -->
               <div class=" relative flex flex-col gap-3 mb-[2.125rem]">
                  <input @blur="mainStore.checkEmail()" @keydown="mainStore.isRightEmail = true"
                     :class="` px-4 ${mainStore.checkValue(mainStore.isRightEmail).txtColor} focus:outline-none`"
                     type="email" placeholder="Email" v-model="mainStore.emailVal">
                  <div :class="` w-full h-px ${mainStore.checkValue(mainStore.isRightEmail).bgColor}`"></div>
                  <h5 v-show="mainStore.isRightEmail == false"
                     class=" absolute bottom-[-20px] px-4 text-neo-error text-[.625rem] leading-[.625rem] tracking-[-.0075rem]">
                     This field is required</h5>
               </div>
               <!-- Pick a date -->
               <div class=" relative flex flex-col items-start gap-2 mb-[2.125rem]">
                  <h4 :class="` ${mainStore.checkValue(mainStore.isRightDate).txtColor}`">
                     Pick a date</h4>
                  <h5 v-show="mainStore.isRightDate == false"
                     class=" absolute bottom-[-20px] text-neo-error text-[.625rem] leading-[.625rem] tracking-[-.0075rem]">
                     This field is incomplete/incorrect</h5>
                  <div class=" flex justify-between w-full">
                     <div class=" flex flex-col gap-[.875rem] w-[27.75%]">
                        <input @blur="mainStore.checkDate()" @keydown="mainStore.isRightDate = true"
                           :class="` w-full px-4 ${mainStore.checkValue(mainStore.isRightDate).txtColor} uppercase focus:outline-none`"
                           type="number" placeholder="mm" v-model="mainStore.monthVal" :min="1" :max="12">
                        <div :class="` w-full h-px ${mainStore.checkValue(mainStore.isRightDate).bgColor}`"></div>
                     </div>
                     <div class=" flex flex-col gap-[.875rem] w-[27.75%]">
                        <input @blur="mainStore.checkDate()" @keydown="mainStore.isRightDate = true"
                           :class="` w-full px-4 ${mainStore.checkValue(mainStore.isRightDate).txtColor} uppercase focus:outline-none`"
                           type="number" placeholder="dd" v-model="mainStore.dayVal" :min="1" :max="31">
                        <div :class="` w-full h-px ${mainStore.checkValue(mainStore.isRightDate).bgColor}`"></div>
                     </div>
                     <div class=" flex flex-col gap-[.875rem] w-[33.5%]">
                        <input @blur="mainStore.checkDate()" @keydown="mainStore.isRightDate = true"
                           :class="` w-full px-4 ${mainStore.checkValue(mainStore.isRightDate).txtColor} uppercase focus:outline-none`"
                           type="number" placeholder="yyyy" v-model="mainStore.yearVal" :min="2023" :max="2025">
                        <div :class="` w-full h-px ${mainStore.checkValue(mainStore.isRightDate).bgColor}`"></div>
                     </div>
                  </div>
               </div>
               <!-- Pick a time -->
               <div class=" relative flex flex-col items-start gap-2 mb-9">
                  <h4 :class="mainStore.checkValue(mainStore.isRightTime).txtColor">
                     Pick a time</h4>
                  <h5 v-show="mainStore.isRightTime == false"
                     class=" absolute bottom-[-20px] text-neo-error text-[.625rem] leading-[.625rem] tracking-[-.0075rem]">
                     This field is incomplete/incorrect</h5>
                  <div class=" flex justify-between w-full">
                     <div class=" flex flex-col gap-[.875rem] w-[27.75%]">
                        <input @blur="mainStore.checkTime()" @keydown="mainStore.isRightTime = true"
                           :class="` w-full px-4 ${mainStore.checkValue(mainStore.isRightTime).txtColor} focus:outline-none`"
                           type="number" placeholder="09" v-model="mainStore.hourVal" :min="0" :max="12">
                        <div class=" w-full h-px bg-neo-inactive"></div>
                     </div>
                     <div class=" flex flex-col gap-[.875rem] w-[27.75%]">
                        <input @blur="mainStore.checkTime()" @keydown="mainStore.isRightTime = true"
                           :class="` w-full px-4 ${mainStore.checkValue(mainStore.isRightTime).txtColor} focus:outline-none`"
                           type="number" placeholder="00" v-model="mainStore.minuteVal" :min="0" :max="59">
                        <div :class="` w-full h-px ${mainStore.checkValue(mainStore.isRightTime).bgColor}`"></div>
                     </div>
                     <div class=" flex flex-col gap-[.875rem] w-[33.5%]">
                        <DropdownTime />
                        <div class=" w-full h-px bg-neo-inactive"></div>
                     </div>
                  </div>
               </div>
               <!-- People counter -->
               <div class=" flex flex-col gap-4 mb-8">
                  <div class=" flex justify-between items-center px-6 select-none">
                     <button @click="mainStore.reducePeople()" class=" h-full p-2">
                        <img :class="mainStore.getLowerMinus" :src="iconMinus" alt="iconMinus">
                     </button>
                     <h4 class=" text-neo-mirage leading-6 tracking-[-.015rem] font-bold">
                        {{ mainStore.peopleCount }} people</h4>
                     <button @click="mainStore.addPeople()" class=" h-full p-2">
                        <img :class="mainStore.getUpperPlus" :src="iconPlus" alt="iconPlus">
                     </button>
                  </div>
                  <div class=" w-full h-px bg-neo-inactive"></div>
               </div>
               <ButtonManager @click="mainStore.submitForm()" btn-type="Light" btn-text="Make reservation"
                  :is-wsize-full="true" />
            </div>
         </div>
      </Transition>
      <!-- - -->
      <RouterLink class=" mt-14 mb-11" to="/">
         <img class=" h-8 select-none " :src="logo" alt="logo" draggable="false">
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
<style>
.fade-enter-active,
.fade-leave-active {
   transition: opacity 1s ease-in-out
}

.fade-enter-from,
.fade-leave-to {
   opacity: 0;
}
</style>