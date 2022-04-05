<template>
  <header class="vw-100">
    <nav class="navbar container-fluid justify-content-between mb-5">
      <div class="logo fs-4">
        <a class="text-uppercase text-decoration-none fw-bold">Boolflix</a>
      </div>
      <div class="search-bar d-flex">
        <input
          v-model.trim="userQuery"
          class="form-control me-2"
          type="search"
          placeholder="Search"
          aria-label="Search"
          @keyup="$emit('search', userQuery)"
        />
        <button
          class="btn btn-outline-danger"
          @click="$emit('search', userQuery)"
          type="submit"
        >
          Search
        </button>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Header",
  data() {
    return {
      userQuery: "",
    };
  },
};
</script>

<style scoped lang="scss">
@import "../assets/style/style.scss";

header {
  background-color: black;

  .logo a {
    color: red;
  }
}
</style>
