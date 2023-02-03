<template>
  <div id="app">
    <input type="text" placeholder="Do zrobienia" v-model="newTask">
    <button @click="addTask">Dodaj</button>
    <ul>
    <li class="task" v-bind:class="{completed: task.completed}" v-for="task in tasks" v-bind:key="task.id">
      <ol>
        {{ task.text }}
        <button @click="">Zrobione</button>
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
        {text: "Zrobić kawe", bool: false, id: 2}
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
    }
  }
}
</script>
<style>
.task {
  border: 1px solid #550000;
  margin: 8px;
  padding: 10px;
}
.completed {
  color: green;

}
</style>