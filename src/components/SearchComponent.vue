<template>
  <div>
    <div class="text-center py-2">
      <label class="c-white">Seleziona il genere: </label>
      <select @change="sendGenre($event)">
        <option value="">all</option>
        <option value="Rock">Rock</option>
        <option value="Pop">Pop</option>
        <option value="Metal">Metal</option>
        <option value="Jazz">Jazz</option>
      </select>
    </div>
  </div>
</template>

<script>
export default {
  name: "SearchComponent",
  data() {
    return {
      selectedGenre: " ",
    };
  },
  methods: {
    sendGenre(event) {
      this.selectedGenre = event.target.value;
      this.$emit("search", this.selectedGenre);
    },
  },
};
</script>

<style>
</style>