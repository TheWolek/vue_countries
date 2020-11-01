<template>
  <div class="infoWrapp">
    <p>{{ info.name }}, {{ this.info.nativeName }}</p>
    <p>{{ info.subregion }}</p>
    <div class="section">
      <div>Area: {{ info.area }} km&sup2;;</div>
      <div>Population: {{ info.population }}</div>
    </div>
    <div class="section">
      <div>Capital {{ info.capital }}</div>
      <div>
        Currencies:
        <span v-for="cur in info.currencies" :key="cur">{{ cur }}</span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "infoComp",
  props: {
    info: Object
  },
  data() {
    return {
      population: ""
    };
  },
  computed: {}
};
</script>

<style lang="scss" scoped>
.infoWrapp {
  display: flex;
  flex-direction: column;

  p {
    margin: 0;
  }
  p + * {
    margin-top: 10px;
  }
  .section {
    display: flex;
    justify-content: center;

    div + div {
      margin-left: 10px;
    }
  }

  .section + .section {
    margin-top: 10px;
  }
}
</style>
