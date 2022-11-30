<template>
  <div>
    <label for="type-filter">Seleziona il genere musicale
      <!-- metodo statico -->
      <!-- <select
        v-model="all"
        @change="songChange"
        id="type-filter"
      >
        <option value="all">TUTTI</option>
        <option value="Rock">ROCK</option>
        <option value="Pop">POP</option>
        <option value="Jazz">JAZZ</option>
        <option value="Metal">METAL</option>
      </select> -->
      <select
        id="type-filter"
        v-model="all"
        @change="songChange"
      >
        <option value="all">TUTTI</option>
        <option
          v-for="genre in arrGenres"
          :key="genre"
          :value="genre"
        >{{ genre }}</option>
      </select>
    </label>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      all: 'TUTTI',
      arrSong: null,
      apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
    };
  },
  computed: {
    arrGenres() {
      const arrGenres = [];
      if (this.arrSong) {
        this.arrSong.forEach((objSong) => {
          if (!arrGenres.includes(objSong.genre)) {
            arrGenres.push(objSong.genre);
          }
        });
      }
      console.log(arrGenres);
      return arrGenres;
    },
  },
  created() {
    axios.get(this.apiUrl)
      .then((axiosResponse) => {
        this.arrSong = axiosResponse.data.response;
      });
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
