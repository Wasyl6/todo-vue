<template>
  <div id="app">
    <h1 v-if="allTasksFinished">Wszystko skończone!</h1>
    <div>
    <input type="text" placeholder="Do zrobienia" v-model="new_task">
    <button @click="addTask">Dodaj</button>
    </div><br>
    <ul>
    <li class="task" v-bind:class="{finished: task.finished}" v-for="task in tasks" v-bind:key="task.id">
      <ol>
        {{ task.text }}
        <input type="checkbox" v-if="!task.finished" @click="removeTask(task.id)">
      </ol>
    </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      new_task: "",
      tasks: [
        {text: "Napisać program", finished: false, id: 1},
        {text: "Zrobić kawe", finished: true, id: 2}
      ]
    }
  },
  methods: {
    addTask() {
      this.tasks.push({
        text: this.new_task,
        finished: false,
        id: Math.random()
      })
      this.new_task = ""
    },
    removeTask(id) {
      const index = this.tasks.findIndex(el => el.id === id)
      this.tasks[index].finished = true
    }
  },
  computed: {
    allTasksFinished() {
    return this.tasks.every(task => task.finished==true)
  }
  }
}
</script>
<style>
#app {
  width: 100%;
  align-content: center;
}
.task {
  color: #f75e5e;
  border: 1px solid #550000;
  margin: 8px;
  padding: 10px;
}
.finished {
  color: green;
  text-decoration: line-through;
}
</style>