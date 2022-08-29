<template>
  <main class="columns is-gapless is-multiline" :class="{ 'dark-mode': isDarkModeOn }">
    <div class="column is-one-quarter">
      <Sidebar @themeChanged="toggleTheme" />
    </div>
    <div class="column is-three-quarter content">
      <RouterView></RouterView>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Sidebar from './components/Sidebar.vue';

export default defineComponent({
  name: "App",
  components: {
    Sidebar,
  },
  data() {
    return {
      isDarkModeOn: false
    }
  },
  methods: {
    toggleTheme(isDarkModeOn: boolean) {
      this.isDarkModeOn = isDarkModeOn;
    }
  }
});
</script>

<style>
main {
  --bg-primary: #FFFFFF;
  --text-primary: #000000;
}

main.dark-mode {
  --bg-primary: #2b2d42;
  --text-primary: #DDDDDD;
}

.content {
  background-color: var(--bg-primary);
}
</style>
