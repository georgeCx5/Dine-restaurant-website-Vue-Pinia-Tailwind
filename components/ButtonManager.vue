<script>
export default {
   data() {
      return {

      }
   }, computed: {
      getType() {
         if (this.btnType == 'Light') {
            return 'bg-neo-cod-gray hover:bg-transparent hover:text-neo-cod-gray border border-neo-cod-gray'
         }
         if (this.btnType == 'Dark') {
            return 'hover:bg-white hover:text-neo-cod-gray border border-white'
         }
      }
   },
   props: {
      btnType: {
         String,
         required: true,
      },
      btnText: {
         String,
         default: 'Empty'
      }
   }
}
</script>
<template>
   <button
      :class="` w-[245px] h-16 ${getType} text-white text-[1rem] leading-[1rem] tracking-[0.15rem] font-semibold uppercase select-none`">
      {{ btnText }}
   </button>
</template>