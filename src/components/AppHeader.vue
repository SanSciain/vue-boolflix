<template>
  <header>
    <div class="container">
      <input
        type="text"
        placeholder="Inseire titolo del film"
        v-model="searchKey"
      />
      <button @click="$emit('buttonClicked', searchKey)">Search</button>
    </div>
  </header>
</template>

<script>
export default {
  name: "AppHeader",
  data() {
    return {
      searchKey: "",
    };
  },
};
</script>

<style lang="scss" scoped>
header {
  background-color: grey;
  padding: 2rem 0;
}
</style>
