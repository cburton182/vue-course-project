<template>
  <div class="container">
    <!-- title prop can be used because it was declared in header component -->
    <Header title="Task Tracker" />
    <!-- v-bind:tasks="tasks" is filling the tasks prop dynamically w/ data  -->
    <Tasks @delete-task="deleteTask" v-bind:tasks="tasks" />
    <!-- @ is shorthand for v-on: -->
    <!-- delete-task is a custom event emitted from Task/Tasks-->
    <!-- This app is structured to propogate an event up from icon in Task Component up to top level where the data exists -->
  </div>
</template>

<script>
import Header from "./components/Header";
import Tasks from "./components/Tasks";
export default {
  name: "App",
  components: {
    Header,
    Tasks,
  },
  data() {
    return {
      tasks: [],
    };
  },
  methods: {
    deleteTask(id) {
      if (confirm("Are you sure?")) {
        this.tasks = this.tasks.filter((task) => task.id !== id);
      }
    },
  },
  created() {
    this.tasks = [
      {
        id: 1,
        text: "Study Vue",
        day: "Feb 18 at 4:30pm",
        reminder: true,
      },
      {
        id: 2,
        text: "Dentis Appointment",
        day: "Feb 19 at 10:30am",
        reminder: true,
      },
      {
        id: 3,
        text: "Fight Bear",
        day: "Feb 20 at 12:00pm",
        reminder: false,
      },
    ];
  },
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
