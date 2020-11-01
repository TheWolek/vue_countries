<template>
  <div class="searchWrapp">
    <h2>Countries</h2>
    <input type="text" v-model="searchText" />
    <input type="button" value="Search" v-on:click="onSearch" />
  </div>
</template>

<script>
export default {
  name: "comp-search",
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

.searchWrapp {
  padding: 20px 0;
  width: 100%;
  height: calc(100vh - 40px);
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;

  input[type="text"] {
    padding: 8px 7px;
    height: 20px;
    font-size: 17px;
    border: 0;
    outline: none;
    border-top-left-radius: 5px;
    border-top-right-radius: 5px;
    border-bottom: 2px solid #000;
    transition: background-color 0.3s ease;

    &:active,
    &:focus {
      background: $InputBg-active;
    }

    &:hover {
      cursor: pointer;
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
    margin-top: 15px;
  }
  h2 {
    margin: 0;
    font-size: 45px;
    margin-bottom: 30px;
  }
}
</style>
