<template>
  <v-container>
    <v-row justify="center">
      <v-col cols="12" md="6">
        <v-card>
          <v-img :src="imageUrl" aspect-ratio="16/9" v-if="imageUrl"></v-img>
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
      imageUrl: null,
    }
  },
  mounted() {
    this.fetchImage()
  },
  methods: {
    async fetchImage() {
      try {
        const response = await axios.get('https://raspberrypi.tail8fca5.ts.net/imgtest/', {
          responseType: 'blob', // バイナリデータとして受け取る
        })

        // Blob を URL に変換
        this.imageUrl = URL.createObjectURL(response.data)
      } catch (error) {
        console.error('画像の取得に失敗しました:', error)
      }
    },
  },
}
</script>

