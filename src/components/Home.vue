<script  lang="ts">
import { ref } from 'vue'
import { defineComponent } from 'vue'
import DateTitle from './DateTitle.vue'

 export default defineComponent({
  name: 'Home',
  components: {
    DateTitle
  },
  data(){
    return {
      loading:true,
      title: 'Global',
      date: '',
      stats: {},
      country: [],
    }
  },
  methods: {
    async fetchCovidData() {
      const result = await fetch('https://api.covid19api.com/summary')
      const dataCovid = await result.json()
      return dataCovid
    }
  },
  async created (){
    const data = await this.fetchCovidData()
    this.date = data.Date
    this.stats = data.Global
    this.country= data.Countries
    this.loading = false

}
})


</script>

<template>
    <main v-if="!loading">
        <DateTitle :text="title" :date="date"></DateTitle>
    </main>
    <main class="flex flex-col" v-else>
        <div class=" m-auto text-gray-500 text-3xl mt-10 mb-6">
            Fetching data
        </div>
        <img class="w-20 m-auto" src="../assets/loading.gif" alt="" srcset="">

    </main>
</template>

<style scoped>

</style>
