<template>
  <InputBar @addTaskObject="addTaskObject" :showModalError="showModalError" />
  <TaskForm :files="files" @removeTaskObject="removeTaskObject" />
</template>
<script>
import InputBar from "./components/InputBar.vue";
import TaskForm from "./components/TaskForm.vue";

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
      timeErrorMsg: 1000,
    };
  },
  methods: {
    removeTaskObject() {
      this.files = this.files.filter((taskObject) => !taskObject.completed);
    },
    addTaskObject(data) {
      this.newTaskObject = data;
      if (this.newTaskObject.trim() === "") {
        this.showModalError = true;
        setTimeout(() => {
          this.showModalError = false;
        }, this.timeErrorMsg);
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
