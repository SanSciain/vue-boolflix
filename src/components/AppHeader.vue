<template>
  <header>
    <div class="container">
      <div class="img-container">
        <img
          src="https://upload.wikimedia.org/wikipedia/commons/7/7a/Logonetflix.png"
          alt="netflix logo"
        />
      </div>

      <div class="input-wrapper">
        <input
          type="text"
          placeholder="Inseire titolo del film"
          v-model="searchKey"
        />
        <button @click="$emit('buttonClicked', searchKey)">Search</button>
      </div>
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
  background-color: black;
  position: sticky;
  .container {
    height: 100px;
    display: flex;
    justify-content: space-between;
    align-items: center;

    .img-container {
      width: 200px;
    }
  }
}
</style>
