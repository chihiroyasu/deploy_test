<template>
  <v-app>
    <v-main>
      <!-- セクション1 -->
      <v-sheet class="mx-auto pa-2 pt-6" color="grey-lighten-4">
        <v-sheet color="grey-lighten-2" height="24" rounded="pill" width="88" />

        <v-slide-group show-arrows>
          <v-slide-group-item
            v-for="(url, index) in poster_path.slice(0, 5)"
            :key="'s1-' + index"
          >
            <v-img
              :src="baseUrl + url"
              class="ma-3"
              height="200"
              width="250"
              style="object-fit: fill;"
            />
          </v-slide-group-item>
        </v-slide-group>
      </v-sheet>

      <!-- セクション2 -->
      <v-sheet class="mx-auto pa-2 pt-6" color="grey-lighten-2">
        <v-sheet color="grey" height="24" rounded="pill" width="88" />

        <v-slide-group show-arrows>
          <v-slide-group-item
            v-for="(url, index) in poster_path.slice(5, 20)"
            :key="'s2-' + index"
          >
            <v-img
              :src="baseUrl + url"
              :width="index === 0 ? 300 : 150"
              class="ma-3"
              height="200"
              style="object-fit: fill;"
            />
          </v-slide-group-item>
        </v-slide-group>

        <!-- グリッド -->
        <v-container fluid>
          <v-row>
            <v-col
              v-for="(url, index) in poster_path.slice(20)"
              :key="'grid-' + index"
              cols="2"
            >
              <v-img
                :src="baseUrl + url"
                height="200"
                width="100%"
                style="object-fit: fill;"
              />
            </v-col>
          </v-row>
        </v-container>
      </v-sheet>
    </v-main>
  </v-app>
</template>

<script>
import axios from 'axios'

export default {
  name: 'ImageDashboard',
  data() {
    return {
      poster_path: [],
      baseUrl: 'https://raspberrypi.tail8fca5.ts.net',
    }
  },
  mounted() {
    this.fetchImages()
  },
  methods: {
    async fetchImages() {
      try {
        const res = await axios.get('https://raspberrypi.tail8fca5.ts.net/posters_info/')
        this.poster_path = res.data.urls || []
      } catch (error) {
        console.error('画像の取得に失敗:', error)
      }
    },
  },
}
</script>
