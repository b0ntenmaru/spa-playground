<template>
  <div class="home">
    <Editor v-model="state.text" @submit="submit" />
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import Editor from '@/components/home/Editor.vue';

export default defineComponent({
  name: 'Home',
  components: {
    Editor,
  },

  setup() {
    const state = reactive<{ text: string }>({
      text: 'hogefuga',
    });

    const submit = (text: string) => {
      console.log(`submit: ${text}`);
    };

    return {
      state,
      submit,
    };
  },
});
</script>
