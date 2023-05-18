<template>
  <button class="button">
    <slot />
  </button>
</template>

<script>
export default {
  name: "u-button",
};
</script>

<style scoped>
.button {
  border: none;
  outline: none;
  font-size: inherit;
  display: inline-block;
  cursor: pointer;
  background: #1f2937;
  text-transform: uppercase;
  color: #fafdff;
  padding: 16px 20px;
  border-radius: 10px;
  transition: 0.3s;
}
.button:hover {
  background: #0c0c14;
}
@media screen and (max-width: 480px) {
  .button {
    padding: 12px 16px;
  }
}
</style>
