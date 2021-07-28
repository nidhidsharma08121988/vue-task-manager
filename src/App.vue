<template>
  <div class="container">
    <Header heading="Task Manager" />
    <AddTask @add-task="addTask" />
    <Tasks
      @toggle-reminder="toggleReminder"
      @delete-task="deleteTask"
      :tasks="tasks"
    />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';
import AddTask from './components/AddTask.vue';
export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data() {
    return {
      tasks: [],
    };
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: 'delectus aut autem',
        day: 'March 1st at 2:30pm',
        reminder: false,
      },
      {
        id: 2,
        text: 'quis ut nam facilis et officia qui',
        day: 'March 3rd at 1:30pm',
        reminder: true,
      },
      {
        id: 3,
        text: 'fugiat veniam minus',
        day: 'March 3rd at 11:00am',
        reminder: false,
      },
      {
        id: 4,
        text: 'et porro tempora',
        day: 'March 1st at 12:30pm',
        reminder: true,
      },
    ];
  },
  methods: {
    deleteTask(id) {
      if (confirm('Are you sure?'))
        this.tasks = this.tasks.filter(task => task.id !== id);
    },
    toggleReminder(id) {
      const updatedTaks = this.tasks.map(task => {
        if (task.id === id) {
          return { ...task, reminder: !task.reminder };
        } else return task;
      });
      this.tasks = updatedTaks;
    },
    addTask(task) {
      this.tasks = [task, ...this.tasks];
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400&display=swap');
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: 'Poppins', sans-serif;
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
