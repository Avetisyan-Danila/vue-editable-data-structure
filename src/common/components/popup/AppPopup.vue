<template>
  <transition name="fade">
    <div
        v-if="modelValue"
        @click.stop="emit('update:modelValue', false)"
        class="popup"
    >
      <div
          @click.stop
          class="popup__content"
      >
        <div
            @click="emit('update:modelValue', false)"
            class="popup__close"
        >&#x2715;</div>

        <slot></slot>
      </div>
    </div>
  </transition>
</template>

<script setup>
defineProps({
  modelValue: {
    type: Boolean,
    default: false
  }
})
const emit = defineEmits(['update:modelValue']);
</script>

<style scoped>
.popup {
  position: fixed;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;

  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;

  background: rgba(0, 0, 0, 0.5);
}

.popup__content {
  position: relative;

  padding: 30px 20px;
  border-radius: 15px;

  background: white;
  box-shadow: 0 0 30px #256a88;
}

.popup__close {
  position: absolute;
  top: 10px;
  right: 20px;

  cursor: pointer;

  color: #256a88;
  transition: 0.4s ease;
}

.popup__close:hover {
  transform: scale(1.20);
}

.fade-enter-active,
.fade-leave-active {
  transition: 0.3s ease-in-out;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

.fade-enter-to,
.fade-leave-from {
  opacity: 1;
}
</style>
