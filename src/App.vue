//App.vue
<template>
  <TaskForm @FormSend="AddTask" />
  <h1>Zadania:</h1>
  <div v-for="(task, index) in tasks" :key="index">
    <Task
      :id="task.id"
      :task="task.taskData"
      :completed="false"
      @DeleteTask="DeleteTask"
      @FinishTask="FinishTask"
    />
  </div>

  <h1>Ukończone zadania</h1>
  <div v-for="(task, index) in finishTasks" :key="index">
    <Task :id="task.id" :task="task.taskData" :completed="true" />
  </div>
</template>

<script>
import Task from "./components/TaskComponent.vue";
import TaskForm from "./components/FormComponent.vue";

export default {
  name: "App",
  data() {
    return {
      tasks: [],
      finishTasks: [],
      currentId: 0,
    };
  },
  components: {
    Task,
    TaskForm,
  },
  methods: {
    AddTask(data) {
      if (data != "") {
        this.tasks.push({ id: this.currentId, taskData: data });
        this.currentId++;
      }
    },
    DeleteTask(id) {
      const taskId = this.tasks.findIndex((a) => a.id == id);
      this.tasks.splice(taskId, 1);
    },
    FinishTask(id) {
      const taskId = this.tasks.findIndex((a) => a.id == id);
      this.finishTasks.push(this.tasks[taskId]);
      this.tasks.splice(taskId, 1);
    },
  },
};
</script>
