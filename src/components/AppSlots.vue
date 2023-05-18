<template>
  <div class="slots">
    <div class="slots__column" v-for="slot in slots" :key="slot">
      <TransitionGroup name="fade">
        <div class="slots__item" v-for="s in slot" :key="s">{{ s }}</div>
      </TransitionGroup>
    </div>
  </div>
</template>

<script>
export default {
  name: "app-slots",
  props: {
    slots: {
      type: Array,
      default: () => [],
      required: true,
    },
  },
};
</script>

<style scoped>
.fade-move,
.fade-enter-active,
.fade-leave-active {
  transition: all 0.5s cubic-bezier(0.55, 0, 0.1, 1);
}
.fade-enter-from,
.fade-leave-to {
  opacity: 0;
  transform: scaleY(0.01) translate(30px, 0);
}
.fade-leave-active {
  position: absolute;
}
.slots {
  display: flex;
  gap: 30px;
  margin: 20px 0;
}
.slots__column {
  display: flex;
  flex-direction: column;
  gap: 30px;
  padding: 10px 20px;
  background: #374151;
  border-radius: 5px;
}
.slots__item {
  font-size: 48px;
}
@media screen and (max-width: 480px) {
  .slots {
    gap: 15px;
    margin: 10px 0;
  }
  .slots__column {
    gap: 15px;
    padding: 5px 10px;
  }
  .slots__item {
    font-size: 36px;
  }
}
</style>
