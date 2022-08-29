<template>
  <div class="box form-container">
    <div class="columns">
      <div class="column" role="form" aria-label="Form to create a new task">
        <input type="text" class="input" placeholder="Describe the activity you're about to start" v-model="taskDescription">
      </div>
      <div class="column">
        <Timer @timerFinished="finishTask" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Timer from './Timer.vue';

export default defineComponent({
  name: 'Form',
  emits: ['onSaveTask'],
  components: {
    Timer
  },
  data() {
    return {
      taskDescription: ''
    }
  },
  methods: {
    finishTask(elapsedTime: number): void {
      this.$emit('onSaveTask', {
        timeInSeconds: elapsedTime,
        description: this.taskDescription
      });
      this.taskDescription =  '';
    }
  }
});
</script>

<style>
.form-container {
  color: var(--text-primary);
  background-color: var(--bg-primary);
}
</style>
