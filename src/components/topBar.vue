<template>
  <div class="topBar">
    <h2>Countries</h2>
    <form v-on:submit.prevent="onSearch" class="topBarSearchWrapp">
      <input type="text" v-model="searchText" />
      <input type="button" value="Search" v-on:click="onSearch" />
      <transition name="fade">
        <div v-if="errorMsg != '' && searchText === ''" class="inputError">
          {{ errorMsg }}
        </div>
      </transition>
    </form>
  </div>
</template>

<script>
export default {
  name: "topBar",
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

  .inputError {
    position: absolute;
    display: flex;
    justify-content: center;
    align-items: center;
    right: 515px;
    top: 60px;
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

.fade-enter-active,
.fade-leave-active {
  transition: all 0.6s ease;
}

.fade-enter,
.fade-leave-to {
  opacity: 0;
}
</style>
