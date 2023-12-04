<template>
  <TaskInputBar @addTaskObject="addTaskObject" :showModalError="showModalError" />
  <TaskForm :files="files" @removeTaskObject="removeTaskObject" />
</template>
<script>
import TaskInputBar from "./components/TaskInputBar.vue";
import TaskForm from "./components/TaskForm.vue";

const TIME_ERROR_MESSAGE = 1000;
export default {
  components: {
    TaskInputBar,
    TaskForm,
  },
  data() {
    return {
      files: [],
      newTask: "",
      showModalError: false,
    };
  },
  methods: {
    removeTaskObject() {
      this.files = this.files.filter((taskObject) => !taskObject.completed);
    },
    addTaskObject(newTask) {

      const isEmpty = newTask.length === 0

      if (isEmpty) {
        this.showModalError = true;

        setTimeout(() => {
          this.showModalError = false;
        }, TIME_ERROR_MESSAGE);
        return;
      }
      const newTaskObject = {
        id: Date.now(),
        task: newTask,
        completed: false,
      };
      this.files.push(newTaskObject);
    },
  },
};
</script>
<style scoped></style>
