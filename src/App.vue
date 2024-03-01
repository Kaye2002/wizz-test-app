<template>
  <div id="app">
    <header>
      <h1>My To-Do List</h1>
      <input v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task" />
      <button @click="addTask">Add</button>
    </header>
    <section>
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          {{ task }}
          <button @click="removeTask(index)">Remove</button>
        </li>
      </ul>
      <div v-if="tasks.length === 0" class="empty-message">No tasks yet. Add some tasks!</div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newTask: "",
      tasks: [],
    };
  },
  methods: {
    addTask() {
      if (this.newTask.trim() !== "") {
        this.tasks.push(this.newTask.trim());
        this.newTask = "";
      }
    },
    removeTask(index) {
      this.tasks.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  text-align: center;
  color: #333;
  margin-top: 50px;
}

header {
  background-color: #3498db;
  padding: 20px;
  color: white;
}

input {
  padding: 10px;
  margin-right: 10px;
  border: 1px solid #3498db;
  border-radius: 4px;
}

button {
  padding: 10px;
  background-color: #3498db;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

section {
  margin-top: 20px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  background-color: #ecf0f1;
  padding: 10px;
  margin: 5px 0;
  border-radius: 4px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

li button {
  background-color: #e74c3c;
  color: white;
  border: none;
  padding: 5px 10px;
  border-radius: 4px;
  cursor: pointer;
}

.empty-message {
  color: #7f8c8d;
  margin-top: 10px;
}
</style>
