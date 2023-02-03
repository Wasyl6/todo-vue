<template>
  <div id="app">
    <input type="text" placeholder="Do zrobienia" v-model="newTaskValue">
    <button @click="addTask">Dodaj</button>
    <ul>
    <li v-for="task in tasks" v-bind:key="task.id">
      <ol>
        {{ task.text }}
      </ol>
    </li>
    </ul>
  </div>
</template>
<script>
import { ref } from 'vue'
const newTaskValue = ref('')
export default {
  data() {
    return {
      tasks: [
        {text: "Napisać program", bool: false, id: 1},
        {text: "Zrobić kawe", bool: false, id: 2}
      ]
    }
  },
  methods: {
    addTask() {
      this.tasks.push({
        text: this.newTaskValue.value,
        bool: false,
        id: Math.random()
      })
      this.newTaskValue.value = ""
    }
  }
}
</script>
