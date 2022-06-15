<template>
    <div class="grid grid-cols-1 md:grid-cols-2 gap-2 mb-10">
        <!-- First Box -->
        <div class="shadow-sm bg-indigo-200 p-10 text-center rounded-md  mx-10 md:ml-20 ">
            <h3 class="text-2xl font-black text-indigo-800 mb-5"> Cases </h3>
            <div class="text-2xl mb-5">
                <span class="font-bold">New:</span>
                {{ number(stats.NewConfirmed) }}
            </div>
            <div class="text-2xl mb-5">
                <span class="font-bold">Total:</span>
                {{ number(stats.TotalConfirmed) }}
            </div>
        </div> 
        <!-- Second Box -->
       <div class="shadow-sm bg-indigo-200 p-10 text-center rounded-md mx-10 md:mr-20 ">
            <h3 class="text-2xl font-black text-indigo-800 mb-5"> Deaths </h3>
            <div class="text-2xl mb-5">
                <span class="font-bold">New:</span>
                {{ number(stats.NewDeaths) }}
            </div>
            <div class="text-2xl mb-5">
                <span class="font-bold">Total:</span>
                {{ number(stats.TotalDeaths) }}
            </div>
        </div> 
      
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

 export default defineComponent({
    name: 'DataBox',
    props: ['stats'],
    methods: {
        number(x: Number){
             return x.toString()
          .replace(/\B(?=(\d{3})+(?!\d))/g, ',');
        }
    }
 })
</script>