<template class="backdrop">
  <v-app >
    <v-app-bar
      app
      color="primary"
      dark
      :src="'https://apod.nasa.gov/apod/image/2107/FlemingsTriangle_Saab_960.jpg'"
    >
    <h1>Spacestagram</h1>
    </v-app-bar>

    <v-main >
      <div v-if='this.loadingStatus' class="loading">
        <h1> Fetching Random NASA Astronomy Pictures of the Day </h1>
        <br />
        <spinner />
      </div>
      <NASAImagesView v-bind:data="this.nasaImages"/>
    </v-main>
  </v-app>
</template>

<script>
import NASAImagesView from './components/NASAImagesView';
import Spinner from 'vue-simple-spinner'
import axios from 'axios'

export default {
  name: 'App',

  components: {
    NASAImagesView,
    Spinner
  },

  methods: {
    async getNASAImages() {
      this.loadingStatus = true

      await axios.get(this.apiUrl)
        .then(response => this.nasaImages = response.data.filter(img => img.media_type == "image"))
        .catch(err => console.log(err)
        );
      
      this.loadingStatus = false
    }
  },

  beforeMount() {
    this.getNASAImages()
  },

  data: () => ({
    apiUrl: "https://api.nasa.gov/planetary/apod?api_key=cV2vrdCjNns2NkRwXh3ytKM7PWs4wlUloU3CftGQ&count=50",
    nasaImages: null,
    loadingStatus: false
  }),
};
</script>

<style scoped>
.loading {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  text-align: center;
}
</style>
