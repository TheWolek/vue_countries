<template>
  <div class="searchWrapp">
    <h2>Countries</h2>
    <input type="text" v-model="searchText" />
    <transition name="fade">
      <div v-if="errorMsg != '' && searchText === ''" class="inputError">
        {{ errorMsg }}
      </div>
    </transition>
    <input type="button" value="Search" v-on:click="onSearch" />
  </div>
</template>

<script>
export default {
  name: "comp-search",
  data() {
    return {
      searchText: "",
      errorMsg: ""
    };
  },
  methods: {
    onSearch() {
      if (this.searchText === "") {
        this.errorMsg = "field is required";
      } else {
        this.errorMsg = "";
        this.$emit("searching", this.searchText);
      }
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

  .inputError {
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    right: 705px;
    top: 465px;
    width: 120px;
    height: 20px;
    background: rgb(214, 88, 88);
    border-radius: 5px;
    border: 2px solid rgb(221, 30, 30);
    font-size: 0.85em;
    padding: 5px 0;
    transition: all 0.3s ease;
    color: rgb(36, 36, 36);
  }

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
    margin-top: 20px;

    &:hover {
      cursor: pointer;
      background: $ctaBg-active;
    }
  }

  h2 {
    margin: 0;
    font-size: 45px;
    margin-bottom: 30px;
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: all 0.6s ease;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
