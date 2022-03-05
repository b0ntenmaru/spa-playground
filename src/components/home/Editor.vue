<template>
  <div class="editor">
    <template v-if="state.mode === 'preview'">
      <div class="preview" @click="changeToModeEdit">
        {{ modelValue }}
      </div>
    </template>
    <template v-if="state.mode === 'edit'">
      <div class="editor">
        <input type="text" :value="modelValue" @input="handleChangeText" />
        <button @click="submit">送信</button>
      </div>
    </template>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';

export default defineComponent({
  name: 'Editor',

  props: {
    modelValue: {
      type: String,
      required: true,
    },
  },

  emits: {
    submit: (text: string) => true,
    'update:modelValue': (modelValue: string) => true,
  },

  setup(props, context) {
    const state = reactive({
      mode: 'preview',
    });

    const changeToModeEdit = () => {
      state.mode = 'edit';
    };

    const changeToModePreview = () => {
      state.mode = 'preview';
    };

    const submit = () => {
      context.emit('submit', props.modelValue);
      changeToModePreview();
    };

    const handleChangeText = (event: Event) => {
      const target = event.target as HTMLInputElement;
      context.emit('update:modelValue', target.value);
    };

    return {
      state,
      changeToModeEdit,
      submit,
      handleChangeText,
    };
  },
});
</script>

<style lang="css">
.preview {
  display: inline-block;
  width: 200px;
  height: 50px;
  border: 1px solid;
  border-radius: 6px;
}

input.editor {
  display: inline-block;
  width: 200px;
  height: 50px;
  border: 1px solid;
  border-radius: 6px;
}
</style>
