<template>
  <div class="container-form">
    <div
      v-show="files.length"
      class="list"
      v-for="taskObject in files"
      :key="taskObject.id"
    >
      <div
        :class="{
          'no-text': taskObject.completed,
          text: !taskObject.completed,
        }"
      >
        <AppCheckBoxForm :toggleCheckBox="taskObject" />
      </div>
      <hr class="lineFormDivisory" />
    </div>
    <AppButton
      buttonClass="secondary"
      :disabled="isTaskListEmpty"
      @click="removeTaskObject"
      >Eliminar completados
    </AppButton>
  </div>
</template>
<script>
import AppCheckBoxForm from './AppCheckBoxForm.vue';
import AppButton from './AppButton.vue';

export default {
  props: {
    files: Object,
  },

  components: { AppButton, AppCheckBoxForm },

  methods: {
    removeTaskObject() {
      this.$emit('removeTaskObject');
    },
    handleSubmit() {
      this.addTaskObject();
    },
  },

  computed: {
    isTaskListEmpty() {
      const tasksCompleted = this.files?.filter(
        (objectToDelete) => objectToDelete.completed,
      );
      return tasksCompleted.length === 0;
    },
  },
};
</script>
<style scoped>
.container-form {
  background-color: white;
  border-radius: 2px;
  margin-bottom: 20px;
  padding-bottom: 50px;
  padding-top: 10px;
  width: 100%;
  box-shadow: 3px 3px 3px lightgray;
}

.list {
  width: 100%;
  color: darkcyan;
  padding-top: 5px;
  padding-inline: 10px;
  position: relative;
  font-size: 17px;
  font-weight: 500;
}

.no-text {
  text-decoration: line-through lightseagreen 2px;
  color: rgb(162, 161, 161);
  padding: 2px;
  font-size: 17px;
  text-overflow: ellipsis;
  white-space: nowrap;
  overflow: scroll;
  margin-right: 20px;
}

.text {
  margin-right: 20px;
  padding: 2px;
}

.lineFormDivisory {
  margin-top: 2px;
  margin-right: 40px;
}

@media (prefers-color-scheme: dark) {
  .list {
    color: cyan;
  }

  .container {
    background-color: dimgrey;
    box-shadow: 3px 3px 3px gray;
  }
}

@media (prefers-color-scheme: dark) {
  .container {
    background-color: dimgrey;
    box-shadow: 3px 3px 3px gray;
  }

  .container-form {
    background-color: dimgrey;
    box-shadow: 3px 3px 3px gray;
  }
}
</style>
