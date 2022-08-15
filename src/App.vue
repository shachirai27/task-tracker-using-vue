<template>
  <div class="container">
    <Header @toggle-add-task="toggleAddTask" title="Task Tracker"
    :showAddTask="showAddTask"/>
    <div v-if="showAddTask">
      <AddTask @add-task="addTask"/>
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from './components/Header'
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask
},
data() {
  return {
    tasks: [],
    showAddTask: false,
  }
},
methods: {
   toggleAddTask() {
    this.showAddTask = !this.showAddTask  
  },
  addTask(task){
    this.tasks = [...this.tasks, task];
  },
  deleteTask(id) {
    if(confirm('Are you sure?')) {
      this.tasks = this.tasks.filter((task)=> 
      task.id != id)
    }
  },
  toggleReminder(id) {
    this.tasks = this.tasks.map((task)=> task.id === id
    ? {...task, reminder: !task.reminder}: task); // spread the task and compare and set reminder
  },
},
created() {
  this.tasks = [
    {
      id: 1,
      text: 'Doctors Appointment',
      day: 'July 27th at 1:00pm',
      reminder: true,
    },
    {
      id: 2,
      text: 'Guitar Class',
      day: 'August 20th at 4:30pm',
      reminder: false,
    },
    {
      id: 3,
      text: 'Meeting with Client',
      day: 'August 21st at 12:00pm',
      reminder: true,
    }
  ]
}
}
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
  background: #94B49F1E;
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
