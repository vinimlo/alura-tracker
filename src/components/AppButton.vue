<template>
  <button class="button" @click="emitClick" :disabled="isDisabled">
    <span class="icon">
      <i :class="iconClasses"></i>
    </span>
    <span>{{ btnText }}</span>
  </button>
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'AppButton',
  emits: ['btnClicked'],
  props: {
    isDisabled: {
      type: Boolean,
      default: false
    },
    btnIcon: {
      type: String,
      required: true
    },
    btnText: {
      type: String,
      required: true
    }
  },
  data() {
    return {
      iconClasses: `fas fa-${ this.btnIcon }`
    }
  },
  methods: {
    emitClick(): void {
      this.$emit('btnClicked')
    }
  }
});
</script>