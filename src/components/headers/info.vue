<script setup>
import { computed } from "vue"

const props = defineProps({
  todos: {
    type: Array,
    required: true,
    default: [],
  },
})

//const todoCount = computed(() => props.todos.length)
//const notodo = computed(() => todoCount.value === 0)
</script>

<!--template>
  <h3 v-if="notodo">目前無任何設備</h3>
  <h3 v-else>目前共計 {{ todoCount }} 項設備</h3>
</template-->
