<script>
export default {
   data() {
      return {
         data: [
            {
               header: 'Seared Salmon Fillet',
               main: 'Our locally sourced salmon served with a refreshing buckwheat summer salad.',
               bg: [
                  'bg-[url(@/assets/images/homepage/salmon-mobile@2x.jpg)]'
               ]
            },
            {
               header: 'Rosemary Filet Mignon',
               main: 'Our prime beef served to your taste with a delicious choice of seasonal sides.',
               bg: [
                  'bg-[url(@/assets/images/homepage/beef-mobile@2x.jpg)]'
               ]
            },
            {
               header: 'Summer Fruit Chocolate Mousse',
               main: 'Creamy mousse combined with summer fruits and dark chocolate shavings.',
               bg: [
                  'bg-[url(@/assets/images/homepage/chocolate-mobile@2x.jpg)]'
               ]
            },
         ]
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
   <article class=" flex flex-col gap-9 h-[418px]">
      <div :class="` w-full h-[245px] ${data[dataIndex].bg} bg-cover bg-center`"></div>
      <div class=" flex flex-col gap-[.375rem] text-center">
         <h3 class=" text-[1.25rem] leading-[1.5rem] tracking-[-.015rem] font-bold">
            {{ data[dataIndex].header }}</h3>
         <p class=" px-8 text-[1rem] leading-[1.625rem]">
            {{ data[dataIndex].main }}
         </p>
      </div>
   </article>
</template>