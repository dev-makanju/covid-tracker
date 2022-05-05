<template>
   <div>
      <div class="grid  md:grid-cols-2 gap-4">
         <!--box-1-->
         <div class="shadow-md bg-blue-500  p-10 text-center rounded">
            <h3 class="text-3xl font-bold mb-4 text-white">Cases</h3>
            <div class="text-2xl mb-4">
               <span class="font-bold text-white">New:</span>
               <span class="ml-4 font-bold text-white">
                  {{ numberWithCommas(stats.NewConfirmed)  }}
               </span>
            </div>
            <div class="text-2xl mb-4">
               <span class="text-white font-bold">Total:</span>
               <span class="ml-4 font-bold text-white">
                  {{numberWithCommas(stats.TotalConfirmed) }}
               </span>
            </div>
         </div>
         <!--box-2-->
         <div class="shadow-md bg-blue-500 p-10 text-center rounded">
            <h3 class="text-3xl  font-bold mb-4 text-white">Death</h3>
            <div class="text-2xl mb-4">
               <span class="text-white font-bold">New:</span>
               <span class="ml-4 text-white">{{ numberWithCommas(stats.NewDeaths) }}</span>
            </div>
            <div class="text-2xl mb-4">
               <span class="font-bold text-white"> Total:</span>
               <span class="ml-4 text-white">{{ numberWithCommas(stats.TotalDeaths) }}</span>
            </div>
         </div>
      </div>
   </div>
</template>

<script>

export default {
   name:'dataBox',
   props:['stats'],
   component:{},
   methods:{
      numberWithCommas(x){
         return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g,',')
      }
   }
}
</script>
