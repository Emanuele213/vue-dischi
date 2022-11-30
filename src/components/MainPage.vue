<template>
  <main class="bg_darkblue">
    <div class="container h-100">
      <div
        v-if="arrSong && selectedValue === 'all'"
        class="row row-cols-5 justify-content-center"
      >
        <SongCard
          v-for="song in arrSong"
          :key="song.author"
          :poster="song.poster"
          :title="song.title"
          :author="song.author"
          :year="song.year"
        />
      </div>
      <div
        v-if="arrSong"
        class="row row-cols-5 justify-content-center"
      >
        <SongCard
          v-for="song in newArrSong"
          :key="song.author"
          :poster="song.poster"
          :title="song.title"
          :author="song.author"
          :year="song.year"
        />
      </div>
      <div
        v-else
        class="d-flex justify-content-center align-items-center h-100"
      >
        <img
          src="@/assets/img/loading.png"
          alt="caricamento"
          class="loading"
        >
      </div>
    </div>
  </main>
</template>

<script>
import SongCard from '@/components/SongCard.vue';
import axios from 'axios';

export default {
  components: {
    SongCard,
  },
  props: {
    selectedValue: String,
  },
  data() {
    return {
      arrSong: null,
      apiUrl: 'https://flynn.boolean.careers/exercises/api/array/music',
    };
  },
  computed: {
    newArrSong() {
      return this.arrSong.filter((eleSong) => eleSong.genre === this.selectedValue);
    },
  },
  created() {
    // scaricare le canzoni
    setTimeout(() => {
      axios.get(this.apiUrl)
        .then((axiosResponse) => {
          console.log(axiosResponse);
          this.arrSong = axiosResponse.data.response;
        });
    }, 2 * 1000);
  },
};
</script>

<style lang="scss" scoped>
.bg_darkblue {
  background-color: #1E2D3B;
  height: 92vh;
}

.row {
  gap: 2rem;
}

.loading {
  height: 100px;
  animation: spin 2s infinite linear;
    @keyframes spin {
        100% {
            transform: rotate(365deg);
        }
    }
}
</style>
