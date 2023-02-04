<template>
  <div id="app">
    <div>
      <h1 class="koniec" v-if="allTasksFinished">Wszystko skończone!</h1>
      <h2>Lista TODO:</h2>
      <input type="text" placeholder="Do zrobienia" v-model="newTaskText">
      <button @click="addTask">Dodaj</button>
    </div><br>
    <ul>
      <li class="task" v-bind:class="{ finished: task.finished }" v-for="task in tasks" v-bind:key="task.id">
        <span v-if="editingTaskId !== task.id || task.finished">{{ task.text }}</span>
        <input type="text" v-model="task.text" v-if="editingTaskId === task.id && !task.finished"/>
        <button v-if="!task.finished" @click="editingTaskId === task.id ? stopEditingTask() : editTask(task.id)">{{ editingTaskId === task.id ? 'Zatwierdz' : 'Edytuj' }}</button>
        <input type="checkbox" v-if="!task.finished" @click="completeTask(task.id)">
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTaskText: "",
      tasks: [],
      editingTaskId: null,
    }
  },
  methods: {
    addTask() {
      this.tasks.push({
        text: this.newTaskText,
        finished: false,
        id: Math.random(),
      })
      this.newTaskText = ""
    },
    completeTask(id) {
      const index = this.tasks.findIndex(task => task.id === id)
      this.tasks[index].finished = true
    },
    editTask(id) {
      this.editingTaskId = id
    },
    stopEditingTask() {
      this.editingTaskId = null
    },
  },
  computed: {
    allTasksFinished() {
      return this.tasks.length > 0 && this.tasks.every(task => task.finished)
    },
  },
}
</script>
