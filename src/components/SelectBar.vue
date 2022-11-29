<template>
  <div>
    <label for="type-filter">Seleziona il genere musicale
      <select
        v-model="all"
        @change="songChange"
      >
        <option value="all">TUTTI</option>
        <option value="Rock">ROCK</option>
        <option value="Pop">POP</option>
        <option value="Jazz">JAZZ</option>
        <option value="Metal">METAL</option>
      </select>
    </label>
  </div>
</template>

<script>
export default {
  data() {
    return {
      all: 'TUTTI',
    };
  },
  methods: {
    songChange() {
      this.$emit('change', this.all);
    },
  },
};
</script>

<style>

</style>
