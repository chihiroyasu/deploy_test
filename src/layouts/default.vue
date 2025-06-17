<template>
  <v-app>
    <Appbar />
    <v-main>
      <router-view />
    </v-main>
    <AppFooter />
  </v-app>
</template>

<script setup>
  //
  import Appbar from '@/components/Appbar.vue';
import AppFooter from '@/components/AppFooter.vue';
</script>
