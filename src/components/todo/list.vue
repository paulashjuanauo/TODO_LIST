<script setup>
const props = defineProps({
  device: {
    type: Object,
    required: true,
  },
})

const emits = defineEmits(["remove-auo-item"])

const remove = () => {
  emits("remove-auo-item", props.device.id)
}
</script>

<template>
  <li
    class="px-10 py-12 bg-white">
    {{ device.title }}
    <button class="px-2 py-1 text-white bg-black" @click="remove">X</button>
  </li>
</template>
