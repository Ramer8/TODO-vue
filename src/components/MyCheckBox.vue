<template>
    <input class="mycheck" type="checkbox" id="checkbox" v-model="toggleCheckBox.completed" />
    <label class="label" for="checkbox">{{ toggleCheckBox.task }}</label>
</template>
<script>
export default {
    props: {
        toggleCheckBox: Object,
    },
};
</script>
<style>
.label {
    position: relative;
    top: -9px;
    margin-left: 5px;
}

.mycheck {
    display: inline-flex;
    align-items: center;
    border-radius: 6px;
    cursor: pointer;
    background-image: url("data:image/svg+xml,%3csvg viewBox='0 0 16 16' fill='lightseagreen' xmlns='http://www.w3.org/2000/svg'%3e%3cpath d='M12.207 4.793a1 1 0 010 1.414l-5 5a1 1 0 01-1.414 0l-2-2a1 1 0 011.414-1.414L6.5 9.086l4.293-4.293a1 1 0 011.414 0z'/%3e%3c/svg%3e");
    width: 24px;
    height: 24px;
    appearance: none;
    border: 3px solid lightseagreen;
    background-position: 0 -9rem;
    background-size: 100%;
    background-repeat: no-repeat;
    transition: all 0.2s ease-in-out;
}

.mycheck:checked {
    background-position: 0 0;
    border: none;
}
</style>
