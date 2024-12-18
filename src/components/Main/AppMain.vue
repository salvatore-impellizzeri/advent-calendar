<script>
import { store } from '../../store';
import Modal from './components/Modal.vue';

export default {
  data() {
    return {
        store,
        modal: false,
    }
  },

  components: {
    Modal,
  },

  methods:{
    openModal(){
      modal = true
    }
  }
}
</script>

<template>
    <div class="grid grid-cols-8 grid-rows-4 gap-6 h-auto py-5 text-center text-white font-semibold">
        <div 
          class="bg-[#2E6754] rounded-lg flex flex-col items-center justify-center" 
          v-for="(day, index) in store.source" 
          :key="index" 
          @click="openModal"
          :class="[index === 24 ? 'bg-[#D4D6F5] col-span-8 text-[#2E6754] aspect-auto' : 'aspect-square']"
        >
            <img :src="day.icon" alt=""
            class="scale-100 h-8"
            >
            <span class="text-4xl">{{ index + 1 }}</span>
        </div> 
    </div>
    <div>
      <Modal v-for="(modal, index) in store.source"
        :gif="modal.url"
        :text="modal.text"
      />
    </div>
</template>


<style scoped>

</style>