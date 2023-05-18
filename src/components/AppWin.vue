<template>
  <div class="win__wrapper">
    <div class="confetti__wrapper">
      <ConfettiExplosion />
    </div>
    <h2 class="title">🤑You Won!🤑</h2>
    <p class="descr">
      To collect your award, follow this
      <a class="link" href="https://youtu.be/AQuBUxl08g8" target="_blank">
        link
      </a>
    </p>
  </div>
</template>

<script>
import ConfettiExplosion from "vue-confetti-explosion";
export default {
  name: "app-win",
  components: { ConfettiExplosion },
};
</script>

<style scoped>
.confetti__wrapper {
  position: absolute;
}
.win__wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.link {
  color: red;
  text-decoration: none;
}
</style>
