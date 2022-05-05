<template>
  <div class="home">
    <main v-if="!loading">
      <dataTitle 
        @close-tab="closeTab()"
        :text="text" 
        :dataDate="dataDate"
        :error="error"
        :errorMessage="errorMessage"
      />
      <dataBoxes :stats="stats"/>
      <CountrySelect @get-country="updateStat" :countries="countries"/>
      <button @click="clearCountryData" v-if="stats.Country" class="bg-blue-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-blue-300">
         Clear County
      </button>
    </main>
    <main class="flex flex-col align-center justify-center" v-else>
        <div class="text-gray-500 text-3xl mt-10 mb-6">
          <div class="w-24 m-auto">
              <h1 class="font-bold text-blue-500">Please wait...</h1>
          </div>
        </div>
    </main>
  </div>
</template>

<script>

// @ is an alias to /src
import dataTitle from '@/components/DataTitle.vue'
import dataBoxes from '@/components/dataBoxes.vue'
import CountrySelect from '@/components/CountySelect.vue'

export default {
  name: 'HomeView',
  components: {
      dataTitle,
      dataBoxes,
      CountrySelect
  },
  data(){
     return{
        error: null,
        errorMessage:'',
        loading: true,
        text: 'Global',
        dataDate:'',
        stats: {},
        countries: [],
        loadingImage: null
     }
  },
  methods:{
    async fetchCovidData(){
      try{
        this.error = false;
        const res = await fetch('https://api.covid19api.com/summary');
        const data = await res.json();
        return data;
      }catch(err){
        this.error = true;
        this.errorMessage = 'Oops, something went wrong Try again',
        console.log(err)
      }
    },
    closeTab(){
      this.error = false;
    },
    updateStat(country){
       this.stats = country
       this.title  = country .Country
    },
    async clearCountryData(){
       this.loading= true;
       const data = this.fetchCovidData()
       this.title = 'Global';
       this.stats = data.Global
       this.loading = false
    }
  },
  async created(){
    const data = await this.fetchCovidData();
    console.log(data)
    this.dataDate = data.Date
    this.stats = data.Global
    this.countries = data.Countries
    this.loading = false;
  },
}
</script>
<style lang="css" scoped>

.home{
   max-width: 1440px ;
   margin: 0px auto;
   width: 90%;
   padding: 10px 10px;
}

@media screen {
  
}

</style>