<script>
import ptDivide from '@/assets/images/patterns/pattern-divide.svg?url'
import ptLines from '@/assets/images/patterns/pattern-lines.svg?url'

export default {
   data() {
      return {
         ptDivide,
         ptLines,
         data: [
            {
               header: ' Enjoyable place for all the family',
               main: 'Our relaxed surroundings make dining with us a great experience for everyone. We can even arrange a tour of the farm before your meal.',
               bg: [
                  'bg-[url(@/assets/images/homepage/enjoyable-place-mobile@2x.jpg)]'
               ]
            },
            {
               header: 'The most locally sourced food',
               main: 'All our ingredients come directly from our farm or local fishery. So you can be sure that you’re eating the freshest, most sustainable food.',
               bg: [
                  'bg-[url(@/assets/images/homepage/locally-sourced-mobile@2x.jpg)]'
               ]
            },
         ],
      }
   },
   props: {
      dataIndex: {
         Number,
         required: true,
      }
   }
}
</script>
<template>
   <article class=" flex flex-col gap-12">
      <div :class="` w-full h-[400px] ${data[dataIndex].bg} bg-cover bg-bottom shadow-2xl`"></div>
      <div class=" flex flex-col items-center text-center">
         <img class=" mb-9 select-none" :src="ptDivide" alt="pattern divide" draggable="false">
         <h2 class=" mb-3 px-10 text-[2rem] leading-[2.5rem] tracking-[-.025rem] font-bold">
            {{ data[dataIndex].header }}</h2>
         <p class=" text-[1rem] leading-[1.625rem]">
            {{ data[dataIndex].main }}
         </p>
      </div>
   </article>
</template>