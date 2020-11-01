<template>
  <div class="imgTile">
    <div class="img" :style="style"></div>
  </div>
</template>

<script>
export default {
  name: "comp-img",
  props: {
    imgSrc: String
  },
  data() {
    return {};
  },
  computed: {
    style() {
      return `backgroundImage: url(${this.imgSrc})`;
    }
  }
};
</script>

<style lang="scss" scoped>
.imgTile {
  width: 100%;
  height: 50vh;
  overflow: hidden;

  .img {
    width: 100%;
    height: 100%;
    background-repeat: no-repeat;
    background-size: cover;
    transition: all 0.3s ease-in-out;
    &:hover {
      transform: scale(1.07);
      cursor: pointer;
    }
  }
}
</style>
