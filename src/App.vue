<script setup>
import { ref, computed } from 'vue';

const lastId = ref(7)
const novoItem = ref('')
const lista = ref([
  { id: 1, text: 'Banana', done: false },
  { id: 2, text: 'Laranja', done: false },
  { id: 3, text: 'Melancia', done: false },
  { id: 4, text: 'Cherimonia', done: false },
  { id: 5, text: 'Granadilha', done: false },
  { id: 6, text: 'Mangostão', done: false },
  { id: 7, text: 'Rambutão', done: false }
])

const ordered = computed(() => [...lista.value].sort((a, b) => a.text > b.text ? 1 : -1))

function adicionarItem() {
  lastId.value++
  lista.value.push({
    id: lastId,
    text: novoItem.value,
    done: false,
  })
  novoItem.value = ''
}
</script>

<template>
  <h1>Lista em ordem alfabetica</h1>
  <ul>
    <li v-for="todo in ordered" :key="todo.id">
      <span :class="{ done: todo.done }"> {{ todo.text }} </span>
    </li>
  </ul>
  <ul>
    <li v-for="todo in lista" :key="todo.id">
      <span :class="{ done: todo.done }"> {{ todo.text }} </span>
    </li>
  </ul>
  <input type="text" v-model="novoItem" />
  <button @click="adicionarItem">+</button>
</template>

<style scoped></style>
