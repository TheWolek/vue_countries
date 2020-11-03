<template>
  <div class="modalBackground">
    <div class="modalWrapp">
      <div class="close" v-on:click="onModalClose"></div>
      <div class="imgContainer" :style="style"></div>
      <div class="details">
        <p>Author: {{ author }}</p>
        <p>Tags: {{ tags }}</p>
        <p><a :href="page" target="_blank">Pixabay</a></p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "modal",
  props: {
    modalImgObject: Object
  },
  data() {
    return {
      src: this.modalImgObject.imgSrc,
      author: this.modalImgObject.author,
      tags: this.modalImgObject.tags,
      page: this.modalImgObject.page
    };
  },
  methods: {
    onModalClose() {
      this.$emit("closeModal");
      console.log("close");
    }
  },
  computed: {
    style() {
      return `background-image: url(${this.src})`;
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
    display: flex;
    justify-content: flex-start;
    align-items: center;
    padding-left: 1.3em;

    .imgContainer {
      width: 75%;
      height: 90%;
      background-repeat: no-repeat;
      background-size: cover;
      border-radius: 5px;
    }

    .details {
      align-self: flex-start;
      margin-top: 4em;
      margin-left: auto;
      margin-right: auto;
      font-size: 1.1rem;

      a,
      a:visited {
        color: inherit;
        text-decoration: none;
        font-weight: bold;
        transition: all 0.2s ease-in-out;

        &:hover {
          color: #000;
        }
      }
    }

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
