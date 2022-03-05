<template>
  <TextField v-model="computedModelValue" />
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';
import TextField from '@/components/home/TextField.vue';

export default defineComponent({
  components: {
    TextField,
  },

  props: {
    modelValue: {
      type: String,
      required: true,
    },
  },

  setup(props, { emit }) {
    const computedModelValue = computed({
      get: () => props.modelValue,
      set: (value: string) => emit('update:modelValue', value),
    });

    return {
      computedModelValue,
    };
  },
});
</script>
