<template>
  <div class="modalBackground">
    <div class="modalWrapp">
      <div class="close"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "modal",
  data() {
    return {};
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

    .close {
      position: absolute;
      top: 10px;
      right: 10px;
      width: 50px;
      height: 50px;
    }
  }
}
</style>
