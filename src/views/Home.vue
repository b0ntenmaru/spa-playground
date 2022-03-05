<template>
  <div class="home">
    <!-- <div>
      text: {{ state.text }}
      <Editor v-model="state.text" @submit="submit" />
    </div> -->

    <div>
      name: {{ state.name }} <br />
      <Child v-model="state.name" />
    </div>

    <div>
      names: {{ state.names }} <br />
      <Checkbox v-model="state.names" value-text="hiroaki" />
      <Checkbox v-model="state.names" value-text="yukari" />
      <Checkbox v-model="state.names" value-text="nanaka" />
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, reactive } from 'vue';
import Editor from '@/components/home/Editor.vue';
import Child from '@/components/home/Child.vue';
import Checkbox from '@/components/home/Checkbox.vue';

export default defineComponent({
  name: 'Home',
  components: {
    // Editor,
    Child,
    Checkbox,
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
