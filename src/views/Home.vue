<template>
  <div class="home">
    <button @click="buttonClick" :disabled="state.disabled">click</button>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

export default defineComponent({
  name: 'Home',

  setup() {
    const state = reactive({
      disabled: false,
    });

    const buttonClick = () => {
      state.disabled = true;

      if (state.disabled) {
        setTimeout(() => {
          console.log('hello');
          state.disabled = false;
        }, 500);
      }
    };

    return {
      buttonClick,
      state,
    };
  },
});
</script>
