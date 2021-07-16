<template>
  <div>
    <h1>Vue Todo With Typescript</h1>
    <TodoInput :item="todoText" @input="updateTodoText"></TodoInput>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import TodoInput from './components/TodoInput.vue';

export default Vue.extend({
  data() {
    return {
      todoText: '',
    };
  },
  components: { TodoInput },
  methods: {
    updateTodoText(value: any) {
      this.todoText = value;
    },
  },
});
</script>

<style scoped></style>
