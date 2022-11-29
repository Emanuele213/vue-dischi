<template>
  <header class="bg_ondark">
    <div
      class="container container-md container-xl d-flex justify-content-between align-items-center"
    >
      <img
        src="@/assets/img/logo-small.svg"
        alt="logo spotify"
      >
      <SelectBar @change="filterSong" />
    </div>
  </header>
</template>

<script>
import SelectBar from '@/components/SelectBar.vue';

export default {
  components: {
    SelectBar,
  },
  data() {
    return {
      arrSong: null,
      value: '',
      apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
    };
  },
  methods: {
    filterSong(selectSong) {
      console.log(selectSong, 'ok');
      this.$emit('change', selectSong);
    },
  },
};
</script>

<style lang="scss" scoped>
.bg_ondark {
  background-color: #2E3A46;
  height: 8vh;
}

.container {
  color: var(--bs-light);
}

img {
  height: 50px;
  margin: 0.8rem;
}
</style>
