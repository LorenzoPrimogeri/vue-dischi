<template>
  <div class="row justify-content-between align-content-center gy-4">
    <div
      v-for="(element, index) in discArray"
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
        <img class="cardImg w-75" :src="element.poster" :alt="element.thumb" />
        <h2 class="m-0 w-100 c-white">{{ element.title }}</h2>
      </div>
      <div class="d-flex flex-wrap w-100">
        <div
          class="d-flex flex-column align-self-end justify-content-center w-100"
        >
          <h4 class="c-grey m-0">{{ element.author }}</h4>
          <span class="c-grey">{{ element.year }}</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "DIscList",
  props: {
    discArray: Array,
  },
};
</script>

<style lang="scss" scoped>
.lp-card {
  width: calc(100% / 5 - 20px);
  height: 420px;
}
.cardImg {
  width: 100%;
}
</style>