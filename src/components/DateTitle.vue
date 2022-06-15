<template>
<div class="text-center">
    <h2 class="text-2xl">
        {{text}}
    </h2>
    <div class="mt-5 mb-10 text-gray-600">
        {{timestamp}}
    </div>
</div>

</template>

<script lang="ts">
import { defineComponent } from 'vue'
import moment from 'moment'

 export default defineComponent({
    name: 'DateTitle',
    props: ['text', 'date'],
    computed: {
        timestamp: function () {
            return moment(this.date).format('h:mm:ss, Do MMMM YYYY')
            
        }
    }
 })


</script>