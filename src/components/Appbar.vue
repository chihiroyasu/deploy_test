<template>
    <v-app-bar class="px-3" density="compact" flat>
      <v-avatar class="hidden-md-and-up" color="grey-darken-1" size="32" />

      <v-spacer></v-spacer>

      <v-tabs align-tabs="center" color="grey-darken-2" v-model="tab">
        <v-tab
          v-for="link in links"
          :key="link.text"
          :to="link.to"
          replace
        >
          {{ link.text }}
        </v-tab>
      </v-tabs>

      <v-spacer></v-spacer>

      <v-avatar class="hidden-sm-and-down" color="grey-darken-1" size="32" />
    </v-app-bar>
</template>

<script setup>
import { ref } from 'vue'

const tab = ref(null)

const links = [
  { text: 'Poster', to: '/poster' },
  { text: 'Poster1', to: '/poster1' },
  { text: 'Poster2', to: '/poster2' },
  { text: 'Demo', to: '/demo' },
]
</script>
