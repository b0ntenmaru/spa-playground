<template>
  <input type="checkbox" v-model="computedModelValue" :value="valueText" />
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';

export default defineComponent({
  props: {
    modelValue: {
      type: Array,
      required: true,
    },

    valueText: {
      type: String,
      required: true,
    },
  },

  emits: {
    'update:modelValue': (modelValue: string[]) => true,
  },

  setup(props, { emit }) {
    const computedModelValue = computed({
      get: () => props.modelValue,
      set: (value: unknown[]) => {
        const modelValue = value as string[];
        emit('update:modelValue', modelValue);
      },
    });

    return {
      computedModelValue,
    };
  },
});
</script>
