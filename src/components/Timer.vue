<template>
  <div class="is-flex is-align-items-center is-justify-content-space-between">
    <Cronometer :timeInSeconds="timeInSeconds" />
    <AppButton :isDisabled="isTimeRunning" :btnIcon="'play'" :btnText="'Start'" @btnClicked="start" />
    <AppButton :isDisabled="!isTimeRunning" :btnIcon="'stop'" :btnText="'Stop'" @btnClicked="stop" />
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue';
import Cronometer from './Cronometer.vue';
import AppButton from './AppButton.vue';

export default defineComponent({
  name: 'Timer',
  components: {
    Cronometer,
    AppButton
  },
  emits: ['timerFinished'],
  data() {
    return {
      timeInSeconds: 0,
      cronometerExecution: 0,
      isTimeRunning: false
    }
  },
  methods: {
    start() {
      this.isTimeRunning = true;
      this.cronometerExecution = setInterval(() => {
        this.timeInSeconds += 1;
      }, 1000);
    },

    stop() {
      this.isTimeRunning = false;
      clearInterval(this.cronometerExecution);
      this.$emit('timerFinished', this.timeInSeconds);
      this.timeInSeconds = 0;
    }
  }
});
</script>