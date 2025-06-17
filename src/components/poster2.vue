<template>
  <v-app> <!-- 必要に応じて -->
    <v-main>
      <!-- セクション1 -->
      <v-sheet class="mx-auto pa-2 pt-6" color="grey-lighten-4">
        <v-sheet color="grey-lighten-2" height="24" rounded="pill" width="88" />

        <v-slide-group show-arrows>
          <v-slide-group-item v-for="n in 6" :key="n">
            <v-img
              :src="baseUrl + poster_path[n % poster_path.length]"
              class="ma-3"
              height="200"
              width="250"
              cover
              rounded
            />
          </v-slide-group-item>
        </v-slide-group>
      </v-sheet>

      <!-- セクション2 -->
      <v-sheet class="mx-auto pa-2 pt-6" color="grey-lighten-2">
        <v-sheet color="grey" height="24" rounded="pill" width="88" />

        <v-slide-group show-arrows>
          <v-slide-group-item v-for="n in 6" :key="n">
            <v-img
              :src="baseUrl + poster_path[n % poster_path.length]"
              :width="n === 1 ? 300 : 150"
              class="ma-3"
              height="200"
              cover
              rounded
            />
          </v-slide-group-item>
        </v-slide-group>

        <v-container fluid>
          <v-row>
            <v-col v-for="n in 12" :key="n" cols="2">
              <v-img
                :src="baseUrl + poster_path[n % poster_path.length]"
                height="200"
                cover
                rounded
              />
            </v-col>
          </v-row>
        </v-container>
      </v-sheet>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const poster_path = ref([])
const baseUrl = 'https://raspberrypi.tail8fca5.ts.net'

onMounted(async () => {
  try {
    const res = await axios.get(baseUrl + '/posters_info/')
    poster_path.value = res.data.urls || []
  } catch (err) {
    console.error('画像の取得に失敗:', err)
  }
})
</script>
