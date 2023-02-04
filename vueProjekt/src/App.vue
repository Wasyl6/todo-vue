<template>
  <div id="app">
    <div>
    <h1 class="koniec" v-if="allTasksFinished">Wszystko skończone!</h1>
    <h2>Lista todo:</h2>
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
      tasks: []
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
      return this.tasks.length > 0 && this.tasks.every(task => task.finished==true)
  }
  }
}
</script>
<style>
#app {
  width: 100%;
  height: 100%;
  text-align: left;
}
.koniec{
  color: gold;
}
.task {
  color: #f75e5e;
  border: 1px solid #550000;
  margin: 5px;
  padding: 5px;
}
.finished {
  color: green;
  text-decoration: line-through;
}
</style>