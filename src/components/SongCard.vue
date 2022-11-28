<template>
  <div class="mod_card text-center">
    <img
      :src="poster"
      :alt="title"
      class="img-fluid"
    >
    <div class="center_card">
      <h3 class="title_card">
        {{ title }}
      </h3>
      <p class="text_card">
        {{ author }}
      </p>
      <p class="text_card">
        {{ year }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    poster: String,
    title: String,
    author: String,
    year: String,
  },
};
</script>

<style lang="scss" scoped>
.mod_card {
  background-color: #2E3A46;
  color: white;
  padding: 1.5rem;
  width: 200px;
  margin-top: 1.5rem;

  .text_card {
    color: lightgray;
  }
}
</style>
