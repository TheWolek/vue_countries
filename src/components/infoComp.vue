<template>
  <div class="infoWrapp">
    <p v-if="info.name === info.nativeName">{{ info.name }}</p>
    <p v-else>{{ info.name }}, {{ info.nativeName }}</p>
    <p>{{ info.subregion }}</p>
    <div class="section">
      <div>Area: {{ info.area }} km&sup2;;</div>
      <div>Population: {{ devidePopulation }}</div>
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
  computed: {
    devidePopulation() {
      let old = this.info.population + "";
      let output = "";
      let counter = 0;
      for (let i = old.length - 1; i >= 0; i--) {
        if (counter == 3) {
          output = old[i] + " " + output;
          counter = 0;
        } else {
          output = old[i] + output;
        }
        counter++;
      }
      return output;
    }
  }
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
