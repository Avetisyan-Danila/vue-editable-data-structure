<template>
  <form
      @submit.prevent="handleSubmitForm"
      class="form"
  >
    <h3 class="form__title">Редактирование {{ props.item.name }}</h3>

    <input
        v-model="inputValue"
        placeholder="Value"
        class="form__input"
    />

    <button class="form__button">Сохранить</button>
  </form>
</template>

<script setup>
import { ref } from "vue";

const props = defineProps({
  item: {
    type: Object,
    required: true
  }
});
const emit = defineEmits(['submit']);

const inputValue = ref(props.item.value);
const handleSubmitForm = () => {
  emit('submit', {name: props.item.name, value: inputValue.value})
};
</script>

<style lang="scss" scoped>
.form {
  width: 300px;
}

.form__title {
  margin: 0 0 10px;
}

.form__input {
  box-sizing: border-box;
  width: 100%;
  padding: 6px 15px;

  font-size: 16px;
  line-height: 24px;
  border: 2px solid #256a88;
  border-radius: 9px;
  transition: 0.4s;

  &:focus {
    outline: none;
    box-shadow: 0 0 5px #256a88;
  }
}

.form__button {
  width: 100%;
  padding: 10px 15px;
  margin-top: 10px;

  cursor: pointer;
  background-color: #256a88;
  font-size: 16px;
  color: #FFFFFF;
  border: none;
  border-radius: 9px;
  transition: 0.4s ease;

  &:hover {
    box-shadow: 0 0 10px #256a88;
  }
}
</style>
