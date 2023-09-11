<script setup>
import todoInfo from "@/components/headers/info.vue"
import todoItem from "@/components/todo/list.vue"
import { v4 as uuidv4 } from "uuid"
import { ref, reactive, onBeforeMount } from "vue"

const todo = ref("")
const todos = reactive([])

const addtodo = () => {
  if (todo.value !== "") {
    console.log(todo.value)
    const item = {
      id: uuidv4(),
      title: todo.value,
      completed: false,
    }
    todos.unshift(item)
    console.log(todos)
    todo.value = ""
  }
}

const removeItem = (id) => {
  const index = todos.findIndex((todo) => {
    return todo.id === id
  })

  todos.splice(index, 1)
}


</script>

<template>
    <main class="container mx-auto">
        <header class="m-2">
            <h1 class="text-6xl font-thin select-none">TODO!</h1>
            <div class="font-semibold select-none text-neutral-600">simple and studid todo app</div>
        </header>
        <form class="px-10 py-12 bg-white shadow-sm">
            <section class="flex">
                <input type="text" placeholder="做點重要的事吧..." class="w-full text-2xl focus:outline-none input-lg input input-bordered" 
                v-model="todo" />
                <button class="text-xl btn-lg btn btn-neutral" @click.prevent="addtodo" >新增</button>
            </section>
        </form>
        
        <section class="px-10 py-6 mt-4 bg-white">
            <header>
            <todoInfo :todos="todos" />
            </header>

            <ul>
            <todoItem
                @remove-auo-item="removeItem"
                v-for="d in todos"
                :todo="d"
            />
            </ul>
        </section>
     
    </main>
</template>

<style scoped></style>
