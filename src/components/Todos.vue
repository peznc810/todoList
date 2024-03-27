<script setup>
import { ref, Transition } from 'vue'

const newTodo = ref('')
const todos = ref([])

const addTodo = () => {
  if (newTodo.value) {
    const id = Math.random()
    todos.value = [{ text: newTodo.value, id }, ...todos.value]
    newTodo.value = ''
  }
}

const deleteTodo = (id) => {
  todos.value = todos.value.filter((todo) => {
    return todo.id !== id
  })
}
</script>

<template>
  <div class="todos">
    <input
      type="text"
      placeholder="Add new todo..."
      class="mb-6 h-10 w-80 rounded-md px-2 text-sm shadow-md transition-shadow duration-200 ease-in focus:shadow-teal-500/50 focus:outline-none"
      v-model="newTodo"
      @keyup.enter="addTodo"
    />
    <Transition name="switch" mode="out-in">
      <div v-if="todos.length">
        <TransitionGroup tag="ul" name="list" appear>
          <li
            v-for="todo in todos"
            :key="todo.id"
            @click="deleteTodo(todo.id)"
            class="mb-4 grid h-12 w-80 place-items-center rounded-md bg-white text-center shadow-md transition-shadow duration-300 ease-in hover:cursor-pointer hover:shadow-lg active:shadow-teal-500/50"
          >
            {{ todo.text }}
          </li>
        </TransitionGroup>
      </div>
      <div v-else class="text-center">
        <span class="opacity-50">There are no tasks...</span>
      </div>
    </Transition>
  </div>
</template>

<style scoped>
/* list animation */
.list-enter-from {
  opacity: 0;
  transform: scale(0.6);
}
.list-enter-to {
  opacity: 1;
  transform: scale(1);
}
.list-enter-active {
  transition: all 0.4s ease;
}

.list-leave-from {
  opacity: 1;
  transform: scale(1);
}
.list-leave-to {
  opacity: 0;
  transform: scale(0.6);
}
.list-leave-active {
  transition: all 1s ease;
}

/* switch List */
.switch-enter-from,
.switch-leave-to {
  opacity: 0;
  transform: translateY(20px);
}
.switch-enter-to,
.switch-leave-from {
  opacity: 1;
  transform: translateY(0px);
}
.switch-enter-active,
.switch-leave-active {
  transition: all 0.4s ease;
}
</style>
