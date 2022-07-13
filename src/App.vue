<template>
  <main class="columns is-gapless is-multiline" :class="{ 'dark-mode': isDarkModeOn }">
    <div class="column is-one-quarter">
      <Sidebar @themeChanged="toggleTheme" />
    </div>
    <div class="column is-three-quarter content">
      <Form @onSaveTask="saveTask"/>
      <div class="list">
        <Task v-for="(task, index) in taskItems" :key="index" :task="task"/>
        <Box v-if="isListEmpty">
          No tasks yet :|
        </Box> 
      </div>
    </div>
  </main>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Sidebar from './components/Sidebar.vue';
import Form from './components/Form.vue';
import Task from './components/Task.vue';
import Box from './components/Box.vue';
import ITask from './interfaces/ITask';

export default defineComponent({
  name: "App",
  components: {
    Sidebar,
    Form,
    Task,
    Box
  },
  data() {
    return {
      taskItems: [] as ITask[],
      isDarkModeOn: false
    }
  },
  computed: {
    isListEmpty(): boolean {
      return this.taskItems.length === 0;
    }
  },
  methods: {
    saveTask(task: ITask) {
      this.taskItems.push(task);
    },
    toggleTheme(isDarkModeOn: boolean) {
      this.isDarkModeOn = isDarkModeOn;
    }
  }
});
</script>

<style>
.list {
  padding: 1.25rem;
}
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
