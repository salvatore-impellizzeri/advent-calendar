<script>
import { store } from '../../store';
import Modal from './components/Modal.vue';

export default {
  data() {
    return {
        store,
        activeIndex: null,
    }
  },

  components: {
    Modal,
  },

  methods:{
    openModal(index){
      this.activeIndex = index;
    },
    
    handleModalClose() {
    this.activeIndex = null;
  },
  }
}
</script>

<template>
    <div class="grid grid-cols-8 grid-rows-4 gap-6 h-auto py-5 text-center text-white font-semibold">
        <div 
          class="bg-[#2E6754] rounded-lg flex flex-col items-center justify-center" 
          v-for="(day, index) in store.source" 
          :key="index" 
          @click="openModal(index)"
          :class="[index === 24 ? 'bg-[#D4D6F5] col-span-8 text-[#2E6754] aspect-auto' : 'aspect-square']"
        >
            <img :src="day.icon" alt=""
            class="scale-100 h-8"
            >
            <span class="text-4xl">{{ index + 1 }}</span>
        </div> 
    </div>
    <div>
      <Modal   
      v-if="activeIndex !== null" 
      :gif="store.source[activeIndex].url" 
      :text="store.source[activeIndex].text" 
      @close="handleModalClose"
      />
    </div>
</template>


<style scoped>

</style>