<template>
  <div class="task" :class="stateClass">
    <span>{{ task.name }}</span>
  </div>
</template>

<script>
export default {
  props: {
    task: {
      type: Object,
      required: true
    }
  },
  computed: {
    stateClass() {
      return {
        pending: this.task.pending,
        done: !this.task.pending
      };
    }
  }
};
</script>

<style>
.task {
  /* Indica que o tamanho do elemento não é só a parte interna e sim as bordas tb */
  box-sizing: border-box;
  width: 350px;
  height: 150px;
  padding: 10px;
  border-radius: 8px;
  font-size: 2rem;
  font-weight: 300;
  cursor: pointer;
  user-select: none; /* Não permite que o usuário selecione o texto */
  display: flex;
  justify-content: center;
  align-items: center;
  /* margin: 10px; */
}
.pending{
  border-left: 12px solid #b73229;
  background-color: #f44336;
}
.done{
  color: #DDD;
  border-left: 12px solid #0a8f08;
  background-color: #4CAF50;
  text-decoration: line-through;
}
</style>