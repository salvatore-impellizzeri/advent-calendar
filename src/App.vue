<script>
import AppHeader from './components/Header/AppHeader.vue';
import AppMain from './components/Main/AppMain.vue';

export default {
  data() {
    return {

    }
  },

  components: {
    AppHeader,
    AppMain,
  }
}
</script>

<template>
  <div class="w-8/12 mx-auto">
    <header>
      <AppHeader />
    </header>
    <main>
      <AppMain />
    </main>
  </div> 
</template>

<style>

</style>

