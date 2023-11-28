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
        <!-- <input class="mycheck" type="checkbox" id="checkbox" v-model="taskObject.completed" />
        <label class="label" for="checkbox"> {{ taskObject.task }}</label> -->
        <CheckBoxForm :toggleCheckBox="taskObject" />
      </div>
      <hr class="lineFormDivisory" />
    </div>
    <CustomButtons
      buttonClass="secondary"
      :disabled="
        !this.files?.filter((objectToDelete) => objectToDelete.completed).length
      "
      @click="removeTaskObject"
      >Eliminar completados</CustomButtons
    >
  </div>
</template>
<script>
import CheckBoxForm from "./CheckBoxForm.vue";
import CustomButtons from "./CustomButtons.vue";

export default {
  props: {
    files: Object,
  },

  components: { CustomButtons, CheckBoxForm },
  methods: {
    removeTaskObject() {
      this.$emit("removeTaskObject");
    },
    handleSubmit() {
      this.addTaskObject();
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
