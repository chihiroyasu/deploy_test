<template>
  <v-container>
    <v-row justify="center">
      <v-col v-for="(index, name) in poster_name" :key="index" cols="12" md="4">
        <v-card>
          <v-img :src="baseUrl + poster_path[index]" aspect-ratio="9/16" v-if="poster_name"></v-img>
          <v-card-text v-else>
            画像を読み込み中です...
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios'

export default {
  name: 'ImageCard',
  data() {
    return {
      poster_name: [],
      poster_path: [],
      baseUrl: 'https://raspberrypi.tail8fca5.ts.net'
    }
  },
  mounted() {
    this.fetch_latest_posters()
  },
  methods: {
    async fetch_latest_posters() {
      try{
        const response = await axios.get('https://raspberrypi.tail8fca5.ts.net/posters_info/');
        this.poster_name = response.data.name;
        this.poster_path = response.data.urls;
      } catch(error) {
        console.error('画像の取得に失敗しました:', error)
      }
    }
  },
}
</script>
