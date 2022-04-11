<template>
  <div class="container-fluid bg-main">
    <div class="container">
      <SearchComponent @search="assignArray" />

      <DiscList :discArray="result" />
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
  /* computed: {
    assignArray() {
      return (this.result = this.filteredGenere());
    },
  },
  methods: {
    filteredGenere() {
      
      const filter = this.result.filter((item) => {
        return item.genre.includes(gen);
      });
      return filter;
    },
  },*/
};
</script>

<style scoped lang="scss">
.container-fluid {
  height: calc(100vh - 82px);
}
</style>
