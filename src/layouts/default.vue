<template>
  <v-main>
    <Appbar>
      <router-view />
    </Appbar>
  </v-main>

  <AppFooter />
</template>

<script setup>
  //
  import Appbar from '@/components/Appbar.vue';
</script>
