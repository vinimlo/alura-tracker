<template>
  <Form @onSaveTask="saveTask" />
  <div class="list">
    <Task v-for="(task, index) in taskItems" :key="index" :task="task" />
    <Box v-if="isListEmpty">
      No tasks yet :|
    </Box>
  </div>
</template>
  
<script lang="ts">
import { defineComponent } from 'vue';
import Form from '../components/Form.vue';
import Task from '../components/Task.vue';
import Box from '../components/Box.vue';
import ITask from '../interfaces/ITask';

export default defineComponent({
  name: "App",
  components: {
    Form,
    Task,
    Box
  },
  data() {
    return {
      taskItems: [] as ITask[]
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
    }
  }
});
</script>
  
<style>
.list {
  padding: 1.25rem;
}
</style>
