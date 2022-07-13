<template>
  <Box>
    <div class="columns">
      <div class="column is-7">
        {{ task.description || 'Task without description' }}
      </div>
      <div class="column">
        <Cronometer :timeInSeconds="task.timeInSeconds" />
      </div>
    </div>
  </Box>

</template>

<script lang="ts">
import { defineComponent, PropType } from 'vue';
import Cronometer from './Cronometer.vue';
import ITarefa from '../interfaces/ITask'
import Box from './Box.vue'

export default defineComponent({
  name: "Task",
  components: {
    Cronometer,
    Box
  },
  props: {
    task: {
      type: Object as PropType<ITarefa>,
      required: true
    }
  }
});
</script>