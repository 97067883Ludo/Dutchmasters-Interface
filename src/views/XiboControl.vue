<template>
  <div class="w-full p-5">
    <div>
      <h2 class="text-3xl text-slate-600 bold">Xibo Control</h2>
    </div>
    <div class="bg-gray-300 h-full rounded-2xl py-3 px-5 mt-2">
    <xibo-api></xibo-api>
    </div>
  </div>
</template>

<script>
import xiboApi from "@/components/Xibo/XiboApi.vue";
export default {
  name: 'Xibo Control',
  data() {
    return {

    }
  },
  components: {
    xiboApi
  }
}
</script>