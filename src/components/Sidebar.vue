<template>
  <header>
    <h1>
      <img src="../assets/logo.png" alt="App logo">
    </h1>
    <button class="button" @click="toggleTheme">
      {{ changeBtnText }}
    </button>
  </header>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'sidebar',
  emits: ['themeChanged'],
  data() {
    return {
      isDarkModeOn: false
    }
  },
  computed: {
    changeBtnText() {
      if(this.isDarkModeOn) {
        return 'Disable dark mode'
      }
      return 'Enable dark mode'
    }
  },
  methods: {
    toggleTheme() {
      this.isDarkModeOn = !this.isDarkModeOn;
      this.$emit('themeChanged', this.isDarkModeOn);
    }
  }
});
</script>

<style scoped>
header {
  padding: 1.5rem;
  background-color: #0d3b66;
  width: 100%;
  height: 100vh;
  text-align: center;
}

header img {
  width: 100px;
}

@media only screen and (max-width: 768px) {
  header {
    padding: 2.5rem;
    height: auto;
  }
}
</style>