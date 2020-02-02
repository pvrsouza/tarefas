<template>
  <div id="app">
    <h1>Tarefas</h1>
    <NewTask @taskAdded="addTask" />
    <TaskGrid :tasks="tasks" />
  </div>
</template>

<script>
import TaskGrid from "./components/TaskGrid";
import NewTask from "./components/NewTask";
export default {
  components: { TaskGrid, NewTask },
  data() {
    return {
      tasks: [
        { name: "Lavar a louça", pending: false },
        { name: "Comprar blusa", pending: true }
      ]
    };
  },
  methods: {
    addTask(task) {
      const sameName = t => t.name === task.name;
      const reallyNew = this.tasks.filter(sameName).length == 0;
      if (reallyNew) {
        this.tasks.push({ name: task.name, pending: task.pendind || true });
      }
    }
  }
};
</script>

<style>
body {
  font-family: "Lato", sans-serif;
  background: linear-gradient(to right, rgb(22, 34, 42), rgb(58, 96, 115));
  color: #fff;
  /* background: #bdc3c7; */ /* fallback for old browsers */
  /* background: -webkit-linear-gradient(to left, #2c3e50, #bdc3c7); */ /* Chrome 10-25, Safari 5.1-6 */
  /* background: linear-gradient(to left, #2c3e50, #bdc3c7); */ /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}

#app {
  display: flex;
  flex: 1;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app h1 {
  margin-bottom: 5px;
  font-weight: 300;
  font-size: 3rem;
}
</style>
