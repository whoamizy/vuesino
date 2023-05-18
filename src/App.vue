<template>
  <div class="container">
    <h1 class="title">🎉Welcome to Vuesino!🎉</h1>
    <p class="descr">Spin now and win big rewards!</p>
    <app-slots :slots="slots" />
    <u-button @click="shuffle">SPIN</u-button>
    <teleport to="#modal-root">
      <Transition>
        <u-modal v-if="isWin" @close="isWin = false">
          <app-win />
        </u-modal>
      </Transition>
    </teleport>
    <span class="author">Made by Whoami</span>
  </div>
</template>

<script>
import UButton from "./components/UI/UButton.vue";
import UModal from "./components/UI/UModal.vue";
import AppWin from "./components/AppWin.vue";
import AppSlots from "./components/AppSlots.vue";
export default {
  name: "App",
  components: { UButton, UModal, AppWin, AppSlots },
  data() {
    return {
      slots: [
        ["✅", "💩", "❌"],
        ["💩", "✅", "❌"],
        ["❌", "💩", "✅"],
      ],
      isWin: false,
    };
  },
  methods: {
    shuffle() {
      this.slots.forEach((slot) => {
        slot.sort(() => Math.random() - 0.5);
      });
    },
    checkWin(slots) {
      let count = 0;
      slots.forEach((slot) => {
        if (this.middleEl(slot) === "✅") {
          count++;
        }
        if (count === slots.length) {
          this.isWin = true;
          return;
        }
        this.isWin = false;
      });
    },
    middleEl(arr) {
      const middleIndex = Math.floor(arr.length / 2);
      return arr[middleIndex];
    },
  },
  watch: {
    slots: {
      handler(newValue) {
        this.checkWin(newValue);
      },
      deep: true,
    },
  },
  created() {
    this.shuffle();
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Kanit:wght@400;700&display=swap");
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: "Kanit", sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 1;
  background: #111828;
  color: #fafdff;
}
.container {
  overflow: hidden;
  padding: 50px 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
.title {
  margin-bottom: 10px;
  font-size: 32px;
}
.descr {
  font-size: 22px;
}
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
.author {
  position: fixed;
  bottom: 20px;
  left: 50%;
  transform: translateX(-50%);
}
@media screen and (max-width: 480px) {
  body {
    font-size: 14px;
  }
  .title {
    font-size: 24px;
  }
  .descr {
    font-size: 16px;
  }
}
</style>
