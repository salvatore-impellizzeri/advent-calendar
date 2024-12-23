<script>
import { store } from '../../store';
import Modal from './components/Modal.vue';

export default {
  data() {
    return {
        store,
        activeIndex: null,
        clickedList: [],
    }
  },

  components: {
    Modal,
  },

  mounted() {
    const savedList = localStorage.getItem('clickedList');
    if (savedList) {
      this.clickedList = JSON.parse(savedList);
    }
  },

  methods:{
    openModal(index){
      this.activeIndex = index;
    },
    
    handleModalClose() {
      this.activeIndex = null;
    },

    handleisClicked(index){
      const alreadyClicked = this.clickedList.find(item => item.cardIndex === index);

      if(!alreadyClicked){
        this.clickedList.push({
          indexCard: index,
          checked: true
        });
      }
      else{
        alreadyClicked.checked = !alreadyClicked.checked;
      }

      localStorage.setItem('clickedList', JSON.stringify(this.clickedList));
    },

    checkingIndex(index) {
      const found = this.clickedList.find(item => item.indexCard === index);
      return found ? found.checked : false;
    }
  }
}
</script>

<template>
    <div class="grid grid-cols-8 grid-rows-4 gap-6 h-auto py-5 text-center text-white font-semibold">
        <button 
          class="bg-[#2E6754] rounded-lg flex flex-col items-center justify-center" 
          v-for="(day, index) in store.source" 
          :key="index" 
          @click="openModal(index), handleisClicked(index)"
          :class="[index === 24 ? 'bg-[#D4D6F5] col-span-8 text-[#2E6754] aspect-auto' : 'aspect-square',
            checkingIndex(index) ? 'bg-transparent' : '',
          ]"
        >
            <img 
              :src="day.icon" 
              :alt="day.type"
              class="scale-100 h-8"
              :class="[checkingIndex(index) ? 'opacity-60' : '']"
            >
            <span 
              class="text-4xl"
              :class="[checkingIndex(index) ? 'opacity-75' : '']"
            >
              {{ index + 1 }}
            </span>
        </button> 
    </div>
    <div>
      <Modal   
        v-if="activeIndex !== null" 
        :gif="store.source[activeIndex]?.url || null" 
        :text="store.source[activeIndex]?.text || null" 
        @close="handleModalClose"
      />
    </div>
</template>


<style scoped>

</style>