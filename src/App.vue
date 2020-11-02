<template>
  <div id="app">
    <transition name="sildeDown">
      <topBar v-if="searching" v-on:searching="onSearch" />
    </transition>
    <transition name="slideUp">
      <search v-if="!searching" v-on:searching="onSearch" />
    </transition>
    <displayResults v-if="searching" v-bind:searchText="SearchFieldOutput" />
  </div>
</template>

<script>
import topBar from "./components/topBar";
import search from "./components/search";
import displayResults from "./components/displayResults";

export default {
  name: "App",
  data() {
    return {
      SearchFieldOutput: "",
      searching: false
    };
  },
  components: {
    search,
    topBar,
    displayResults
  },
  methods: {
    onSearch(e) {
      this.SearchFieldOutput = e;
      this.searching = true;
      //console.log(this.SearchFieldOutput);
    }
  }
};
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  background: rgb(243, 243, 243);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.slideUp-enter-active,
.slideUp-leave-active {
  transition: all 0.5s ease;
}

.slideUp-enter,
.slideUp-leave-to {
  transform: translateY(-70vh);
  opacity: 0;
}

.sildeDown-enter-active,
.sildeDown-leave-active {
  transition: all 0.6s ease;
}

.sildeDown-enter,
.sildeDown-leave-top {
  transform: translateY(-100px);
  opacity: 1;
}
</style>
