<template>
  <InputBar @addTaskObject="addTaskObject" :showModalError="showModalError" />
  <TaskForm :files="files" @removeTaskObject="removeTaskObject" />
</template>
<script>
import InputBar from "./components/InputBar.vue";
import TaskForm from "./components/TaskForm.vue";

const timeErrorMsg = 1000;
export default {
  components: {
    InputBar,
    TaskForm,
  },
  data() {
    return {
      files: [],
      newTaskObject: "",
      showModalError: false,
    };
  },
  methods: {
    removeTaskObject() {
      this.files = this.files.filter((taskObject) => !taskObject.completed);
    },
    addTaskObject(data) {
      this.newTaskObject = data;

      const emptyInput = this.newTaskObject.length;
      if (emptyInput === 0) {
        this.showModalError = true;
        setTimeout(() => {
          this.showModalError = false;
        }, timeErrorMsg);
        return;
      }

      this.newTask = {
        id: Date.now(),
        task: this.newTaskObject,
        completed: false,
      };
      this.files.push(this.newTask);
    },
  },
};
</script>
<style scoped></style>
