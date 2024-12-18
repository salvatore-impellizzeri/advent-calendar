<script>
export default {
  data() {
    return {
      close: false,
    }
  },

  props: {
    gif: String,
    text: String
  },
  methods: {
    closeModal() {
      this.close = !this.close;
    },
  },
};
</script>

<template>
  <div v-if="!closeModal" class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center z-50">
    <div 
      class="flex flex-col gap-7 justify-center items-center rounded-2xl bg-white py-7 px-5"
      style="width: 400px;"
    >
      <div class="w-full">
        <img v-if="gif"
          :src="gif" 
          alt="Gif"
          class="w-full h-auto object-contain"
        >
        <div v-if="text">
          <span>{{ text }}</span>
        </div>
      </div>
      <button 
        @click="closeModal"
        class="bg-red-600 py-2 px-7 rounded-full text-white text-lg font-semibold"
      >
        Chiudi
      </button>
    </div>
  </div>
</template>

<style scoped>
</style>
