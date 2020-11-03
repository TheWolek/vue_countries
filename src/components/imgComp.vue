<template>
  <div class="imgTile">
    <div class="img" :style="style" v-on:click="onImgClick"></div>
  </div>
</template>

<script>
export default {
  name: "comp-img",
  props: {
    imgSrc: String,
    id: Number,
    imgAuthor: String,
    imgTags: String,
    imgPage: String
  },
  data() {
    return {
      imgObject: {
        imgSrc: this.imgSrc,
        id: this.id,
        author: this.imgAuthor,
        tags: this.imgTags,
        page: this.imgPage
      }
    };
  },
  methods: {
    onImgClick() {
      this.$emit("imgClicked", this.imgObject);
    }
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
