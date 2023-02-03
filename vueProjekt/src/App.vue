<template>
  <div id="app">
    {{ newTask }}
    <input type="text" placeholder="todo" v-model="newTask">
    <button @click="newTask">Dodaj</button>
    <div v-for="task in tasks" v-bind:key="task.id">
      <ol>
        {{ task.text }}
      </ol>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      newTask: "aaa",
      tasks: [
        {text: "Napisać program", bool: false, id: 1},
        {text: "Zrobić kawe", bool: false, id: 2}
      ]
    }
  },
  methods: {
    newTask(){
      this.tasks.push({
        text: this.newTask,
        bool: false,
        id: Math.random()
      })
      this.newTask = ""
    }
  }
}
</script>
