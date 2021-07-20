<template>
  <li>
    <span>{{ todo }}</span>
    <button @click="deleteTodoItem">삭제</button>
  </li>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  props: {
    todo: {
      type: String,
      default: '',
    },
    todoIndex: {
      type: Number,
      default: 0,
    },
  },
  methods: {
    deleteTodoItem() {
      this.$emit('delete', this.todoIndex);
    },
  },
});
</script>

<style scoped></style>
