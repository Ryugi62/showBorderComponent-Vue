<template>
  <div class="border-box" v-show="isShow">
    <div class="combo-box">
      <input type="text" v-model="inputValue" />
      <button class="apply" @click="applyBorder">적용</button>
    </div>

    <button class="close" @click="toggleBox">x</button>
  </div>
</template>

<script>
export default {
  name: "BorderComponent",
  data() {
    return {
      isShow: false,
      inputValue: "",
    };
  },

  mounted() {
    document.addEventListener("keydown", this.toggleShowOnF9);
  },

  unmounted() {
    document.removeEventListener("keydown", this.toggleShowOnF9);
  },

  methods: {
    toggleShowOnF9(e) {
      if (e.key === "F9") this.toggleBox();
    },

    applyBorder() {
      this.inputValue = this.inputValue ? this.inputValue : "*";
      this.clearBorders();
      this.applyBorders(this.inputValue);
      this.clearBorders(".border-box, .border-box *");
      this.inputValue = "";
    },

    clearBorders(selector = "*") {
      document.querySelectorAll(selector).forEach((el) => {
        el.style.border = "";
      });
    },

    applyBorders(selector) {
      document.querySelectorAll(`${selector}, ${selector} *`).forEach((el) => {
        el.style.border = el.style.border ? "" : "1px solid red";
      });
    },

    toggleBox() {
      this.isShow = !this.isShow;
      this.isShow ? this.applyBorder() : this.clearBorders();
    },
  },
};
</script>

<style scoped>
button {
  border: 0;
  outline: 0;
}

.border-box {
  right: 10px;
  width: fit-content;
  border: 1px solid black;
  padding: 25px;
  position: fixed;
  background: white;
  border-radius: 5px;
}

.combo-box {
  border: 1px solid rgb(150, 150, 150);
  display: flex;
}

.combo-box input {
  border: 0;
  outline: 0;
}

.combo-box button {
  color: white;
  background-color: #4caf50;
}

.combo-box button:hover {
  background-color: #46a049;
}

.combo-box button:active {
  background-color: #3e8e41;
}

.close {
  top: 0;
  right: 0;
  position: absolute;
  background-color: transparent;
}
</style>
