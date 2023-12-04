<template>
  <div class="container" @submit.prevent="$emit('addTaskObject', newTask)">
    <div class="input-bar">
      <input type="text" v-model="newTask" @keypress.enter="$emit('addTaskObject', newTask)" />
      <AppButton buttonClass="primary" @click="$emit('addTaskObject', newTask)">Añadir
      </AppButton>
    </div>
  </div>
  <AppErrorComponent v-show="showModalError">Ingrese una tarea por favor
  </AppErrorComponent>
</template>

<script>
import AppButton from "./AppButton.vue";
import AppErrorComponent from "./AppErrorComponent.vue";

export default {
  props: {
    showModalError: Boolean,
  },

  emits: ["addTaskObject"],

  components: {
    AppButton,
    AppErrorComponent,
  },

  data() {
    return {
      newTask: "",
    };
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
