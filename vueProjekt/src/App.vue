<template>
  <div id="app">
    <input type="text" placeholder="todo" v-model="newTask">
    <button @click="">Dodaj</button>
    <div v-for="task in tasks" v-bind:key="task.id">
      <ol>
      {{ item.title }}
      </ol>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      newTask: null,
      tasks: [
        {title: "Napisać program", completed: false, id:"1"},
        {title: "Zrobić kawe", completed: false, id:"2"}
      ]
    }
  },
  methods: {
    newTask(){

    }
  }
}
</script>
