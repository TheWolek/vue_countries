<template>
  <div class="results">
    <div v-if="errorMsg != '' && countryPhotos.length === 0">
      nothing was found, please try again
    </div>
    <div v-else-if="errorMsg != ''">
      {{ errorMsg }}
    </div>
    <div v-else>Results for {{ searchText }}:</div>
    <infoComp v-if="infoReady" :info="countryDetail" />

    <div class="resultsImgs">
      {{ query }}
      <imgComp
        v-for="photo in countryPhotos"
        :img-src="photo.largeImageURL"
        :img-author="photo.user"
        :img-tags="photo.tags"
        :img-page="photo.pageURL"
        :key="photo.id"
        v-on:imgClicked="onImgClick"
      />
    </div>
  </div>
</template>

<script>
import imgComp from "./imgComp";
import infoComp from "./infoComp";

export default {
  name: "displayResults",
  components: {
    imgComp,
    infoComp
  },
  props: {
    searchText: String
  },
  data() {
    return {
      countryDetail: {},
      countryPhotos: [],
      infoReady: false,
      errorMsg: ""
    };
  },
  methods: {
    onImgClick(e) {
      this.$emit("imgClicked", e);
    }
  },
  computed: {
    query() {
      this.infoReady = false;
      this.errorMsg = "";
      let page = Math.floor(Math.random() * 10);
      page <= 0 ? (page += 1) : page;

      fetch(`https://restcountries-v1.p.rapidapi.com/name/${this.searchText}`, {
        method: "GET",
        headers: {
          "x-rapidapi-host": "restcountries-v1.p.rapidapi.com",
          "x-rapidapi-key": "5ef2a4c054mshb06cd533d70f5cbp1ef2fajsnbcc298d14203"
        }
      })
        .then(response => {
          if (response.status === 404) {
            this.infoReady = false;
            throw new Error(
              `Only pictures for the ${this.searchText} term were found:`
            );
          } else {
            return response.json();
          }
        })
        .then(response => {
          //console.log("res: ", response);
          this.countryDetail = response[0];
          this.infoReady = true;
        })
        .catch(err => {
          console.log(err);
          this.errorMsg = err.message;
        });

      fetch(
        `https://pixabay.com/api/?key=18929159-7903855673a1b0ee32e462f41&q=${this.searchText}&page=${page}&category=nature&per_page=20&image_type=photo`,
        {
          method: "GET"
        }
      )
        .then(response => response.json())
        .then(response => {
          console.log(response);
          this.countryPhotos = response.hits;
        })
        .catch(err => {
          console.log(err);
        });
    }
  }
};
</script>

<style lang="scss" scoped>
.results {
  margin-top: 80px;
  width: 100%;
}
.resultsImgs {
  width: 80%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  grid-template-rows: auto;
  grid-gap: 15px;
  margin-left: auto;
  margin-right: auto;
  margin-top: 20px;
}
</style>
