<template>
  <div class="data-card">
    <div
        @click="$emit('openForm', item)"
        class="data-card__edit"
    >
      <img width="20" height="20" src="@/assets/edit.svg" alt="Редактировать">
    </div>
    <div class="data-card__name"><b>name: </b>{{ item.name }}</div>
    <div class="data-card__value"><b>value: </b>{{ item.value }}</div>
  </div>
</template>

<script setup>
defineProps({
  item: {
    type: Object,
    required: true
  }
});
defineEmits(['openForm']);
</script>

<style scoped lang="scss">
.data-card {
  position: relative;
  padding: 20px 40px 20px 20px;

  border: 3px solid #256a88;
  border-radius: 12px;
}

.data-card__edit {
  position: absolute;
  top: 20px;
  right: 20px;

  width: 20px;
  height: 20px;
  cursor: pointer;
  opacity: 0;
  transition: 0.4s ease;

  img {
    width: 100%;
    height: 100%;
  }

  @media (min-width: 1024px) {
    &:hover {
      transform: scale(1.1);
    }
  }

  @media (max-width: 1024px) {
    opacity: 1;
  }
}

.data-card:hover .data-card__edit {
  opacity: 1;
}

.data-card__name,
.data-card__value {
  word-break: break-word;
}
</style>
