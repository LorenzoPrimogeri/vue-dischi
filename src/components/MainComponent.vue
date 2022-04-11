<template>
  <div class="container-fluid bg-main">
    <div class="container">
      <SearchComponent @search="filteredGenere" />
      <div class="row justify-content-between align-content-center gy-4">
        <div
          v-for="(element, index) in result"
          :key="index"
          class="
            lp-card
            bg-grey
            text-center
            d-flex
            flex-column
            justify-content-between
            align-content-center
          "
        >
          <div class="py-3">
            <img
              class="cardImg w-75"
              :src="element.poster"
              :alt="element.thumb"
            />
            <h2 class="m-0 w-100 c-white">{{ element.title }}</h2>
          </div>
          <div class="d-flex flex-wrap w-100">
            <div
              class="
                d-flex
                flex-column
                align-self-end
                justify-content-center
                w-100
              "
            >
              <h4 class="c-grey m-0">{{ element.author }}</h4>
              <span class="c-grey">{{ element.year }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
//https://flynn.boolean.careers/exercises/api/array/music
import axios from "axios";
import SearchComponent from "./SearchComponent.vue";
export default {
  name: "MainComponent",
  components: {
    SearchComponent,
  },
  data() {
    return {
      result: [],
      genereSelezionato: "",
    };
  },
  mounted() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        this.result = response.data.response;
        console.log(this.result);
      });
  },
  methods: {
    filteredGenere(genereSelezionato) {
      console.log(genereSelezionato);
      const filter = this.result.filter((item) => {
        return item.genre.includes(this.genereSelezionato);
      });

      return filter.filter((item) => {
        item.genre.includes(this.genereSelezionato);
        console.log(filter);
      });
    },
  },
};
</script>

<style scoped lang="scss">
.lp-card {
  width: calc(100% / 5 - 20px);
  height: 420px;
}
.container-fluid {
  height: calc(100vh - 82px);
}
.cardImg {
  width: 100%;
}
</style>
