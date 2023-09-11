<script setup>
import imgUrl from '@/assets/images/delete.png'
const props = defineProps({
  todo: {
    type: Object,
    required: true,
  },
})

const emits = defineEmits(["remove-auo-item"])

const remove = () => {
  emits("remove-auo-item", props.todo.id)
}
</script>

<template>
  <li
    class="flex items-center justify-between py-6 border-b">
    <div class="flex item-center gap-3">
      <input type="checkbox"  class="checkbox" v-model="todo.completed" :id="todo.id"/>
      <label class="text-xl cursor-pointer" :class="{'completed':todo.completed}">{{ todo.title }}</label>
     
    </div>
    <div>
      <button class="px-2 py-1 text-white" @click="remove"><img :src="imgUrl" alt=""  class="w-6 h-6"></button>
    </div>
    





  </li>
</template>

<style>
  .completed {
    text-decoration: line-through
  }
</style>
