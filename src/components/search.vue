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
.searchWrapp {
  padding: 20px 0;
  input + input {
    margin-left: 15px;
  }
  h2 {
    margin: 0;
  }
}
</style>
