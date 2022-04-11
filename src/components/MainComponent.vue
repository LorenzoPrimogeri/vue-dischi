<template>
  <div class="container-fluid bg-main">
    <div class="container">
      <SearchComponent @search="filteredGenere" />
      <DiscList :discArray="filteredArray" />
    </div>
  </div>
</template>

<script>
//https://flynn.boolean.careers/exercises/api/array/music
import axios from "axios";
import SearchComponent from "./SearchComponent.vue";
import DiscList from "./DiscList.vue";
export default {
  name: "MainComponent",
  components: {
    SearchComponent,
    DiscList,
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
  computed: {
    filteredArray() {
      const filter = this.result.filter((item) => {
        return item.genre.includes(this.genereSelezionato);
      });
      return filter;
    },
  },
  methods: {
    filteredGenere(gen) {
      this.genereSelezionato = gen;
    },
  },
};
</script>

<style scoped lang="scss">
.container-fluid {
  height: calc(100vh - 82px);
}
</style>
