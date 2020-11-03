<template>
  <div class="modalBackground">
    <div class="modalWrapp">
      <div class="close" v-on:click="onModalClose"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "modal",
  data() {
    return {};
  },
  methods: {
    onModalClose() {
      this.$emit("closeModal");
      console.log("close");
    }
  }
};
</script>

<style lang="scss" scoped>
.modalBackground {
  position: fixed;
  top: 0;
  z-index: 3;
  width: 100%;
  height: 100vh;
  background: rgba(192, 192, 192, 0.384);

  .modalWrapp {
    position: fixed;
    top: 50%;
    left: 50%;
    z-index: 4;
    width: 70%;
    height: 700px;
    background: rgb(247, 247, 247);
    transform: translate(-50%, -50%);
    border-radius: 10px;
    transition: all 0.3s ease;

    .close {
      position: absolute;
      top: 10px;
      right: 10px;
      width: 40px;
      height: 40px;
      display: inline-block;
      overflow: hidden;

      &:hover {
        cursor: pointer;
      }

      &::before,
      &::after {
        content: "";
        position: absolute;
        height: 3px;
        width: 100%;
        top: 50%;
        left: 0;
        margin-top: -1px;
        background: #000;
      }
      &::before {
        transform: (rotate(45deg));
      }
      &::after {
        transform: (rotate(-45deg));
      }
    }
  }
}
</style>
