<script  lang="ts">
import { ref } from 'vue'
import { defineComponent } from 'vue'


 export default defineComponent({
  // type inference enabled
//   props: {
//     name: String,
//     msg: { type: String, required: true }
//   },
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
    <main>
        hola
    </main>
</template>

<style scoped>

</style>
