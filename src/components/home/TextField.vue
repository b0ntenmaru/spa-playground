<template>
  <input type="text" :value="modelValue" @input="handleChangeText" />
</template>

<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'TextField',

  props: {
    modelValue: {
      type: String,
      required: true,
    },
  },

  emits: {
    'update:modelValue': (updatedModelValue: string) => true,
  },

  setup(_, { emit }) {
    const handleChangeText = (event: Event) => {
      const target = event.target as HTMLInputElement;
      emit('update:modelValue', target.value);
    };

    return {
      handleChangeText,
    };
  },
});
</script>
