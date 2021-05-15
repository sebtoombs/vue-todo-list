<template>
  <div class="py-10 px-6 mx-auto max-w-3xl">
    <VStack spacing="1rem">
      <form @submit="handleAddTodoSubmit">
        <div class="flex items-end">
          <div class="flex-grow mr-3">
            <label for="newTaskName" class="font-medium mb-1 block text-xl"
              >Add a task</label
            >
            <Input
              v-model="state.newTaskName"
              placeholder="e.g. Learn Vue"
              id="newTaskName"
            />
          </div>
          <div>
            <Button type="submit" colorScheme="green">Add todo</Button>
          </div>
        </div>
      </form>
      <div class="flex justify-end">
        <div class="mr-6">
          <dl>
            <dt class="font-medium text-sm">Total tasks</dt>
            <dd class="font-semibold text-3xl">1</dd>
          </dl>
        </div>
        <div>
          <dl>
            <dt class="font-medium text-sm">Completed tasks</dt>
            <dd class="font-semibold text-3xl">1</dd>
          </dl>
        </div>
      </div>
      <VStack spacing="0.5rem">
        <TodoItem
          v-for="(todoItem, index) in state.todoList"
          :key="index"
          :id="index"
          :removeTodo="removeTodo"
        >
          {{ todoItem.taskName }}
        </TodoItem>
      </VStack>
    </VStack>
  </div>
</template>

<script setup>
import { reactive } from "vue";
import Input from "./components/Input.vue";
import VStack from "./components/VStack.vue";
import Button from "./components/Button.vue";
import TodoItem from "./components/TodoItem.vue";

const TODO_STATUS = {
  incomplete: "incomplete",
  complete: "complete",
};

const TODO_PRIORITY = {
  urgent: "urgent",
  high: "high",
  normal: "normal",
  low: "low",
};

const Todo = ({
  taskName = "",
  status = TODO_STATUS.incomplete,
  priority = TODO_PRIORITY.normal,
}) => {
  return {
    taskName,
    status,
    priority,
  };
};

const state = reactive({
  todoList: [],
  sortBy: null,
  sortDir: null,
  newTaskName: "",
});

const addTodo = (taskName) => {
  state.todoList.push(Todo({ taskName }));
};

const removeTodo = (index) => {
  state.todoList.splice(index, 1);
};

const handleAddTodoSubmit = (e) => {
  e.preventDefault();
  if (!state.newTaskName) return;
  addTodo(state.newTaskName);
  state.newTaskName = "";
};
</script>
