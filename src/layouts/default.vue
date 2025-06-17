<template>
  <v-main>
    <Appbar theme="dark" />
    <router-view />
  </v-main>

  <AppFooter />
</template>

<script setup>
  //
  import Appbar from '@/components/Appbar.vue';
</script>
