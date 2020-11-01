<template>
  <div class="topBar">
    <h2>Countries</h2>
    <div class="topBarSearchWrapp">
      <input type="text" v-model="searchText" />
      <input type="button" value="Search" v-on:click="onSearch" />
    </div>
  </div>
</template>

<script>
export default {
  name: "topBar",
  data() {
    return {
      searchText: ""
    };
  },
  methods: {
    onSearch() {
      this.$emit("searching", this.searchText);
    }
  }
};
</script>

<style lang="scss" scoped>
$InputBg-active: rgb(247, 247, 247);
$ctaBg: rgb(84, 219, 145);
$ctaBg-active: rgb(106, 226, 160);

.topBar {
  position: fixed;
  top: 0;
  width: 100vw;
  background: rgb(226, 226, 226);
  z-index: 2;
  display: flex;
  justify-content: space-around;
  align-items: center;

  h2 {
    font-size: 25px;
  }
  .topBarSearchWrapp {
    input[type="text"] {
      padding: 7px;
      height: 18px;
      font-size: 17px;
      border: 0;
      outline: none;
      border-radius: 5px;
      transition: background-color 0.3s ease;

      &:active,
      &:focus {
        background: $InputBg-active;
      }

      &:hover {
        cursor: text;
        background: $InputBg-active;
      }
    }

    input[type="button"] {
      width: 80px;
      padding: 10px 8px;
      background: $ctaBg;
      outline: none;
      border: none;
      border-radius: 5px;
      transition: background-color 0.3s ease;

      &:hover {
        cursor: pointer;
        background: $ctaBg-active;
      }
    }

    input + input {
      margin-left: 15px;
    }
  }
}
</style>
