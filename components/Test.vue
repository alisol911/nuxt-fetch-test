<script setup>

const props = defineProps({
  id: String
})

const todoId = ref(props.id == "1" ? 1 : 2)
const { data, pending, error } = await useFetch(() => `https://jsonplaceholder.typicode.com/todos/${todoId.value}`, { key: props.id } )

onBeforeUpdate(() => {
  console.log(`onBeforeUpdate id: ${props.id} todoId: ${todoId.value}`)
})

onUpdated(() => {
  console.log(`onUpdated id: ${props.id} todoId: ${todoId.value}`)
})

</script>

<template>
  <div>
    id: {{ props.id }}
    todoId <input v-model="todoId"/>
    
    <text>{{ data }}</text>
  </div>
</template>
