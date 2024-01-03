//TaskComponent.vue
<template>
  <div class="task">
    <h2>ZADANIE: {{ id }}</h2>
    <h3>{{ task }}</h3>

    <div v-if="!completed">
      <button @click="FinishTask">Zakończ zadanie</button>
      <button @click="DeleteTask">Usuń zadanie</button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    task: String,
    id: Number,
    completed: Boolean,
  },
  methods: {
   DeleteTask() {
      this.$emit("DeleteTask",this.$props.id);
    },
    FinishTask() {
      this.$emit("FinishTask",this.$props.id);
    },
  },
};
</script>

<style scoped>
.task {
  border: 1px solid black;
  margin: 10px 0;
  padding: 0 10px;
  padding-bottom: 10px;
}
</style>
