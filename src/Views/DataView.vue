<template>
  <p class="hint">Наведите на карточку, чтобы редактировать</p>

  <div class="data">
    <data-card
        v-for="item in data"
        :key="item.name"
        :item="item"
        @open-form="handleOpenForm"
    />
  </div>

  <app-popup v-model="isFormVisible">
    <data-form
        :item="itemToEdit"
        @submit="handleSubmitForm"
    />
  </app-popup>
</template>

<script setup>
import DataCard from "@/modules/data/components/DataCard.vue";
import AppPopup from "@/common/components/popup/AppPopup.vue";
import DataForm from "@/modules/data/components/DataForm.vue";
import { ref } from "vue";

defineProps({
  data: {
    type: Array,
    required: true
  }
});
const emit = defineEmits(['updateData']);

const isFormVisible = ref(false);
const itemToEdit = ref(null);

const handleOpenForm = (item) => {
  isFormVisible.value = true;
  itemToEdit.value = item;
};
const handleSubmitForm = (item) => {
  isFormVisible.value = false;
  emit('updateData', item);
};
</script>

<style scoped lang="scss">
.hint {
  text-align: center;
  margin-bottom: 40px;

  @media (max-width: 1024px) {
    display: none;
  }
}

.data {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 20px;

  max-width: 800px;
  margin: 0 auto;

  @media (max-width: 1024px) {
    grid-template-columns: repeat(2, 1fr);
  }

  @media (max-width: 576px) {
    grid-template-columns: 1fr;
  }
}
</style>
