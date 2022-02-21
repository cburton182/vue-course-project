<!-- <Tasks @delete-task="deleteTask" v-bind:tasks="tasks" /> -->
<template>
  <div :key="task.id" v-for="task in tasks">
    <!-- tasks is a prop defined in parent component -->
    <!-- tasks array will be looped, each test will create a Task and assidgn a key -->
    <Task @delete-task="$emit('delete-task', task.id)" :task="task" />
  </div>
</template>

<script>
import Task from "./Task";
export default {
  name: "Tasks",
  props: {
    tasks: Array,
  },
  components: {
    Task,
  },
  emits: ["delete-task"],
  //   emits array needed when propogating up?
};
</script>
