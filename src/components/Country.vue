<template>
    <div class=" grid grid-cols-1 w-screen">
        <select @change="onChange" v-model="selected" class="p-3 rounded mB-10 mx-10 md:mx-20">
            <option value="0">Select Country</option>
            <option v-for="country in countries" :value="country.ID">
            {{country.Country}}</option>
        </select>
    </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

 export default defineComponent({
    name: 'Country',
    props: ['countries'],
    data(){
        return{
            selected: 0
        }
    },
    methods: {
        onChange(){
            const country = this.countries.find((item:any) => item.ID === this.selected)
            this.$emit('get-country',country)

        }
    }

 })
</script>