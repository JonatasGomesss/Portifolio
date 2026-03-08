<template>
  <v-app class="app-background">
    <v-main class="main-content">
      <router-view />
    </v-main>
  </v-app>
</template>

<script lang="ts" setup>
  //
</script>

<style>
.app-background {
  min-height: 100vh;
  background: radial-gradient(circle at top, #111827 0, #020617 55%, #020617 100%);
  color: #f9fafb;
}

.main-content {
  background-color: transparent !important;
}

.post {
  background-color: transparent;
}
</style>
