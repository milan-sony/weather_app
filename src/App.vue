<template>
  <div class="bg-blue-400 h-dvh">
    <SiteNavigation />
  </div>
  <RouterView />
</template>

<script>
import { RouterView } from 'vue-router'

// components
import SiteNavigation from './components/SiteNavigation.vue'

export default {
  name: 'App',
  components: {
    SiteNavigation
  }
}
</script>