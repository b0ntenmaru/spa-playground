<template>
  <div class="home">
    <div>
      text: {{ state.text }}
      <Editor v-model="state.text" @submit="submit" />
    </div>

    <div>
      checked: {{ state.name }} <br />
      <TextField v-model="state.name" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import Editor from '@/components/home/Editor.vue';
import TextField from '@/components/home/TextField.vue';

export default defineComponent({
  name: 'Home',
  components: {
    Editor,
    TextField,
  },

  setup() {
    const state = reactive({
      text: 'hogefuga',
      names: ['hiroaki'],
      name: 'hiroaki',
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
