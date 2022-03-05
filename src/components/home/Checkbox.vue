<template>
  <input
    type="checkbox"
    :value="valueText"
    @input="handleCheckModelValue"
    :checked="checked"
  />
</template>

<script lang="ts">
import { computed, defineComponent } from 'vue';

export default defineComponent({
  name: 'Checkbox',

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

  setup(props, { emit }) {
    const checked = computed(() => {
      return props.modelValue.includes(props.valueText);
    });

    const handleCheckModelValue = (event: Event) => {
      const target = event.target as HTMLInputElement;

      if (target.checked) {
        emit('update:modelValue', [...props.modelValue, target.value]);
      } else {
        const newModelValue = props.modelValue.filter(
          (item) => item !== target.value
        );
        emit('update:modelValue', newModelValue);
      }
    };

    return {
      handleCheckModelValue,
      checked,
    };
  },
});
</script>
