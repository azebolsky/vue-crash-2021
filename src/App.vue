<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTasks" />
    <div v-if="showAddTasks">
      <AddTask @add-task="addTask" />
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
import AddTask from "./components/AddTask";

export default {
  name: "App",
  components: {
    Header,
    Tasks,
    AddTask
  },
  // data is a function
  data() {
    return {
      tasks: [],
      showAddTasks: false
    };
  },
  methods: {
    toggleAddTask() {
      this.showAddTasks = !this.showAddTasks;
    },
    addTask(newTask) {
      this.tasks = [...this.tasks, newTask];
    },
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter(task => task.id !== id);
      }
    },
    toggleReminder(id) {
      this.tasks = this.tasks.map(task =>
        task.id === id ? { ...task, reminder: !task.reminder } : task
      );
    }
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Adam",
        day: "March 1st at 2:30pm",
        reminder: true
      },
      {
        id: 2,
        text: "Sammie",
        day: "March 3rd at 2:30pm",
        reminder: true
      },
      {
        id: 3,
        text: "Ripley",
        day: "March 4th at 2:30pm",
        reminder: false
      }
    ];
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap");
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: "Poppins", sans-serif;
}

.container {
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  padding: 30px;
  border-radius: 5px;
}
.btn {
  display: inline-block;
  background: #000;
  color: #fff;
  border: none;
  padding: 10px 20px;
  margin: 5px;
  border-radius: 5px;
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}
.btn:focus {
  outline: none;
}
.btn:active {
  transform: scale(0.98);
}
.btn-block {
  display: block;
  width: 100%;
}
</style>
