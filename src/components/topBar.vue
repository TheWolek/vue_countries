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
.topBar {
  position: fixed;
  top: 0;
  width: 100vw;
  background: rgb(226, 226, 226);
  z-index: 2;
  display: flex;
  justify-content: space-around;
  align-items: center;
  .topBarSearchWrapp {
    input + input {
      margin-left: 15px;
    }
  }
}
</style>
