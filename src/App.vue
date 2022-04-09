<template>
  <div id="app">
    <HeaderComponent />
    <MainComponent />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";
export default {
  name: "App",
  components: {
    HeaderComponent,
    MainComponent,
  },
};
</script>

<style lang="scss">
.bg-grey {
  background-color: hsl(210deg 21% 23%);
}
.bg-main {
  background-color: hsl(209deg 33% 17%);
}
.c-white {
  color: white;
}
.c-grey {
  color: grey;
}
</style>
