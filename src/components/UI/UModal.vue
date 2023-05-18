<template>
  <div class="modal__overlay">
    <div class="modal__content">
      <slot />
      <u-button @click="$emit('close')">SPIN AGAIN</u-button>
    </div>
  </div>
</template>

<script>
import UButton from "./UButton.vue";
export default {
  name: "u-modal",
  components: { UButton },
};
</script>

<style scoped>
.modal__overlay {
  display: flex;
  align-items: center;
  justify-content: center;
  position: fixed;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  width: 100%;
  height: 100%;
  padding: 15px;
  background: rgba(0, 0, 0, 0.5);
}
.modal__content {
  min-width: 300px;
  min-height: 100px;
  background: #fafdff;
  color: #111828;
  padding: 20px 24px;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}
@media screen and (max-width: 480px) {
  .modal__content {
    padding: 10px 14px;
  }
}
</style>
