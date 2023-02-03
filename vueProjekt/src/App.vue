<template>
  <div id="app">
    <input type="text" placeholder="Do zrobienia" v-model="newTask">
    <button @click="addTask">Dodaj</button>
    <ul>
    <li class="task" v-bind:class="{finished: task.bool}" v-for="task in tasks" v-bind:key="task.id">
      <ol>
        {{ task.text }}
        <button v-if="!task.bool" @click="removeTask(task.id)">Zrobione</button>
      </ol>
    </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: [
        {text: "Napisać program", bool: false, id: 1},
        {text: "Zrobić kawe", bool: true, id: 2}
      ]
    }
  },
  methods: {
    addTask() {
      this.tasks.push({
        text: this.newTask,
        bool: false,
        id: Math.random()
      })
      this.newTask = ""
    },
    removeTask(id) {
      const index = this.tasks.findIndex(el => el.id === id)
      this.tasks[index].bool = true
    }
  }
}
</script>
<style>
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