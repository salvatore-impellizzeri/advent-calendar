<script>
import { store } from '../../store';

export default {
  data() {
    return {
        store,
    }
  },

  components: {

  },

  methods:{

  }
}
</script>

<template>
    <div class="grid grid-cols-8 grid-rows-4 gap-6 h-auto py-5 text-center text-white font-semibold">
        <div 
        class="bg-[#2E6754] rounded-lg flex flex-col items-center justify-center aspect-square" 
        v-for="(day, index) in store.source" 
        :key="index" 
        :class="[index === 24 ? 'bg-[#D4D6F5] col-span-8 text-[#2E6754] aspect-auto' : '']"
        >
            <img :src="day.icon" alt=""
            class="scale-100 h-8"
            >
            <span class="text-4xl">{{ index + 1 }}</span>
        </div> 
    </div>
</template>


<style scoped>

</style>