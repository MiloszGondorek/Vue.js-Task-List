// FormComponent.vue
<template>
  <form @submit.prevent="SendForm">
    <h1>Dodaj zadanie:</h1>
    <p><span>Treść zadania</span><input type="text" v-model="taskData" /></p>
    <button>Dodaj zadanie</button>
  </form>
</template>

<script>
export default {
  data() {
    return {
      taskData: "",
    };
  },
  methods: {
    SendForm() {
      this.$emit("FormSend", this.taskData);
      this.taskData="";
    },
  },
};
</script>
