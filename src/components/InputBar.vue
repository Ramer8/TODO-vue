<template>
  <div class="container" @submit.prevent="addTaskObject">
    <div class="input-bar">
      <input type="text" v-model="newTaskObject" @keyup.enter="addTaskObject" />
      <CustomButtons buttonClass="primary" @click="addTaskObject">Añadir
      </CustomButtons>
    </div>
  </div>
  <ErrorComponent v-show="showModalError">Ingrese una tarea por favor</ErrorComponent>
</template>

<script>
import CustomButtons from "./CustomButtons.vue";
import ErrorComponent from "./ErrorComponent.vue";

export default {
  props: {
    files: Object,
  },

  emits: ["input"],

  components: {
    CustomButtons,
    ErrorComponent,
  },

  data() {
    return {
      newTaskObject: "",
      showModalError: false,
      timeErrorMsg: 1000,
    };
  },
  methods: {
    addTaskObject() {
      if (this.newTaskObject.trim() === "") {
        this.showModalError = true;
        setTimeout(() => {
          this.showModalError = false;
        }, this.timeErrorMsg);
        return;
      }
      this.files.push({
        id: Date.now(),
        task: this.newTaskObject,
        completed: false,
      });
      this.newTaskObject = "";
    },
  },
};
</script>
<style scoped>
.container {
  background-color: white;
  border-radius: 2px;
  margin-bottom: 20px;
  padding: 13px;
  display: flex;
  box-shadow: 3px 3px 3px lightgray;
}

.input-bar {
  width: 100%;
  display: flex;
  max-width: 100%;
  position: relative;
}

.input-bar input {
  display: block;
  padding: 1rem 2rem;
  width: 100%;
  background: whitesmoke;
  border: none;
  color: black;
  text-align: left;
  text-decoration: none;
  font-size: 19px;
  outline: white;
  border-radius: 2px;
}

@media (prefers-color-scheme: dark) {
  .container {
    background-color: dimgrey;
    box-shadow: 3px 3px 3px gray;
  }
}

@media (prefers-color-scheme: dark) {
  .input-bar input {
    background-color: grey;
  }

  .container {
    background-color: dimgrey;
    box-shadow: 3px 3px 3px gray;
  }
}
</style>
