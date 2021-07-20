<template>
  <div>
    <header>
      <h1>Vue Todo With Typescript</h1>
    </header>
    <main>
      <TodoInput
        :item="todoText"
        @input="updateTodoText"
        @add="addTodoItem"
      ></TodoInput>
      <div>
        <ul>
          <TodoListItem
            v-for="(todoItem, index) in todoItems"
            :key="index"
            :todoItem="todoItem"
            :todoIndex="index"
            @toggle="toggleTodoItemComplete"
            @remove="removeTodoItem"
          />
        </ul>
      </div>
    </main>
  </div>
</template>

<script lang="ts">
import Vue from 'vue';
import TodoInput from './components/TodoInput.vue';
import TodoListItem from './components/TodoListItem.vue';

const STORAGE_KEY = 'vue-todo-ts-v1';
const storage = {
  save(todoItems: Todo[]) {
    const parsed = JSON.stringify(todoItems);
    localStorage.setItem(STORAGE_KEY, parsed);
  },
  fetch(): Todo[] {
    const todoItems = localStorage.getItem(STORAGE_KEY) || '[]';
    const result = JSON.parse(todoItems);

    return result;
  },
};

export interface Todo {
  title: string;
  done: boolean;
}

export default Vue.extend({
  data() {
    return {
      todoText: '',
      todoItems: [] as Todo[],
    };
  },
  components: { TodoInput, TodoListItem },
  methods: {
    updateTodoText(value: string) {
      this.todoText = value;
    },
    addTodoItem() {
      const todo: Todo = {
        title: this.todoText,
        done: false,
      };
      this.todoItems.push(todo);

      storage.save(this.todoItems);
      this.initTodoText();
    },
    initTodoText() {
      this.todoText = '';
    },
    fetchTodoItems() {
      this.todoItems = storage.fetch().sort((a, b) => {
        if (a.title < b.title) {
          return -1;
        }
        if (a.title < b.title) {
          return 1;
        }

        return 0;
      });
    },
    removeTodoItem(todoIndex: number) {
      this.todoItems.splice(todoIndex, 1);

      storage.save(this.todoItems);
    },
    toggleTodoItemComplete(todoItem: Todo, todoIndex: number) {
      this.todoItems.splice(todoIndex, 1, {
        ...todoItem,
        done: !todoItem.done,
      });

      storage.save(this.todoItems);
    },
  },
  created() {
    this.fetchTodoItems();
  },
});
</script>

<style scoped></style>
