<template>
  <v-container>
    
    <v-row>
      <v-col
        v-for="i in data" 
        :key="i.url"
        cols="i.flex"
      >
        <image-card
            :title="i.title" 
            :date="i.date"
            :desc="i.explanation"
            :url="i.url"
            />
      </v-col>
    </v-row>

  </v-container>
</template>

<script>
import ImageCard from './ImageCard.vue'

export default {
  components: { ImageCard },
  name: 'NASAImagesView',

  props: {
    data: Array
  },

  data: () => ({
     //
  }),
}
</script>
