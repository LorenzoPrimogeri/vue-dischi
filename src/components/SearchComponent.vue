<template>
  <div>
    <div class="text-center py-2">
      <label class="c-white">Seleziona il genere: </label>
      <select @change="sendGender($event)">
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
      selectedGender: " ",
    };
  },
  methods: {
    sendGender(event) {
      this.selectedGender = event.target.value;
      this.$emit("search", this.selectedGender);
    },
  },
};
</script>

<style>
</style>