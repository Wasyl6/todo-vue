<template>
  <div id="app">
    <input type="text" placeholder="todo" v-model="newTask">
    <button @click="newTask">Dodaj</button>
    <div v-for="task in tasks" v-bind:key="task.id">
      <h2>
        {{ task.title }}
      </h2>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: [
        {title: "Napisać program", boolean: false, id: 1},
        {title: "Zrobić kawe", boolean: false, id: 2}
      ]
    }
  },
  methods: {
    newTask(){
      this.tasks.push({
        title: this.newTask,
        boolean: false,
        id: Math.random()
      })
      this.newTask = ""
    }
  }
}
</script>
