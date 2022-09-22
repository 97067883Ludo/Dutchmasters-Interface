<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <nav-bar class="w-60 fixed" />
  <section class="ml-60 h-full"><RouterView /></section>


</template>

<script>
import NavBar from "@/components/NavBar.vue";
export default {
components: {
  NavBar
}
}
</script>