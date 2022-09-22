<template>
  <div class="min-h-full pl-5 pt-5 bg-gray-300">
    <h1 class="text-3xl bold text-slate-600">Dutchmasters</h1>
    <h2 class="text-xl bold text-slate-600">Dashboard</h2>
    <div v-for="page in pages" class="mt-5 w-full">
      <RouterLink :to=page.url>
        <div :class="this.checkForRoute(page)" class="p-3 rounded-l-xl mt-2 w-full mx-auto">
          {{page.name}}
        </div>
      </RouterLink>
    </div>
  </div>
</template>

<script>
import router from "@/router";
  export default{
    data() {
      return {
        pages: {
          'home': {
            'name': 'Home',
            'url': '/'
          },
          'obs': {
            'name': 'Obs-Control',
            'url': '/obs-control'
          },
          'xibo': {
            'name': 'Xibo-Control',
            'url': '/xibo-control'
          }
        }
      }
    },
    methods: {
      checkForRoute(page)
      {
        return page.url == this.$route.path ? 'bg-white' : 'bg-gray-400';

      },
      updateTimeEverySecond()
      {

      }
    }
  }
</script>