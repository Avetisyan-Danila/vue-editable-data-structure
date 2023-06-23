<template>
  <data-view
      :data="data"
      @update-data="handleUpdateData"
  />
</template>

<script setup>
import dataMocks from "@/mocks/data.json"
import DataView from "@/Views/DataView.vue";
import { ref } from "vue";

const data = ref(dataMocks);

const handleUpdateData = (newItem) => {
  const index = data.value.findIndex((item) => item.name === newItem.name);
  data.value.splice(index, 1, newItem);
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-size: 18px;
}
</style>
