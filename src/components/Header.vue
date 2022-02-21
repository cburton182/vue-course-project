<template>
  <header>
    <!-- title is a prop that will be defined where this compenent is exported: in this case App.vue -->
    <h1>{{ title }}</h1>
    <!-- text and color are props that were declared in button component and are now being defined.  Now this button can be used elsewhere with different text and color -->
    <Button text="Add Task" color="green" />
  </header>
</template>

<script>
import Button from "./Button";
export default {
  name: "Header",
  props: {
    title: String,
    // title: {
    //   type: String,
    //   default: "Hello World!",
    // },
  },
  components: {
    Button,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 20px;
}
</style>
