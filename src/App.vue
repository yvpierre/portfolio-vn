<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import Header from "@/components/Header.vue";
</script>

<template>
  <link href="https://api.fontshare.com/v2/css?f[]=cabinet-grotesk@1,800,500,100,700,400,300,200,900&display=swap" rel="stylesheet">
  <Header />
  <div>
    <h1>TEST</h1>
    red
  </div>
  <RouterView />
</template>

<style lang="scss" scoped>

</style>
