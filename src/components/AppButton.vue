<template>
  <button :class="buttonClass" :disabled="disabled">
    <slot></slot>
  </button>
</template>
<script>
export default {
  props: {
    disabled: Boolean,
    buttonClass: String,
  },
};
</script>
<style>
button {
  border: none;
  padding: 10px;
  font-size: 16px;
  border-radius: 8px;
  cursor: pointer;
  transition: opacity 0.25s;
}

button:hover {
  opacity: 0.7;
}

button[disabled] {
  cursor: not-allowed;
  opacity: 0.5;
}

button[disabled]:hover {
  opacity: 0.2;
}

.primary {
  background-color: lightpink;
  border: none;
  padding: 10px;
  border-radius: 8px;
  cursor: pointer;
}

.button-completed-false {
  border: 3px solid lightseagreen;
  color: lightseagreen;
  margin-right: 10px;
  border-radius: 6px;
  margin-left: 8px;
}

.button-completed-true {
  color: lightseagreen;
  margin-right: 6px;
  border-radius: 6px;
  font-size: 12px;
  margin-left: 8px;
}

.secondary {
  background-color: darkcyan;
  border-radius: 6px;
}

.container-form .secondary {
  position: absolute;
  position: -webkit-sticky;
  margin-left: 20px;
  margin-top: 6px;
}

.input-bar Button {
  display: block;
  height: 70%;

  position: absolute;
  right: 2%;
  transform: translateX(-10%);
  top: 17%;
}

@media (prefers-color-scheme: light) {
  .button-completed-true {
    background-color: white;
  }

  .button-completed-false {
    background-color: white;
  }

  button {
    color: white;
  }
}

@media (prefers-color-scheme: dark) {
  .button-completed-true {
    background-color: dimgray;
  }

  .button-completed-false {
    background-color: dimgray;
  }
}
</style>
