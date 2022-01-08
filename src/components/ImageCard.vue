<template>
  <v-card
    outlined
    elevation="3"
    >
      <a :href="this.url" target="_blank">
        <v-img
            max-height=750
            max-width="auto"
            :src="this.url"
            contain
            class="grey darken-4"
            :alt="this.title"
            >
            <template v-slot:placeholder>
                <v-row
                class="fill-height ma-0"
                align="center"
                justify="center"
                >
                <v-progress-circular
                    indeterminate
                    color="grey lighten-5"
                ></v-progress-circular>
                </v-row>
            </template>
        </v-img>
      </a>
  
    <v-card-title> {{ this.title }} </v-card-title>

    <v-card-text> {{ this.date }} </v-card-text>

    <v-divider class="mx-4"/>

    <v-card-text> {{ this.desc }} </v-card-text>

    <v-card-text>
        <v-btn
            v-bind:style="[this.imageLiked ? {'background-color': 'red', 'color': 'white'} : {'background-color': 'white'} ]"
            @click="liked()"
            
        >
        <v-icon>
            mdi-heart
        </v-icon>
            {{ this.likeBtnText }}
        </v-btn>
    </v-card-text>

    </v-card>
</template>

<script>
export default {
    name: 'ImageCard',

    props: {
      title: String,
      date: String,
      desc: String,
      url: String
    },

    methods: {
        liked() {
            this.imageLiked = !this.imageLiked
            if (this.imageLiked) {
                this.likeBtnText = "UnLike"
            } else {
                this.likeBtnText = "Like"
            }
        }
    },

    data: () => ({
      imageLiked: false,
      likeBtnText: "Like"
    }),
}
</script>

<style>

</style>