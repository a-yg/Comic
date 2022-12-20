<script lang="ts">
// import CloudTwitter from '../components/CloudTwitter.vue'
// import CloudWorld from '../components/CloudWorld.vue'
import ComicTop from '../pages/ComicTop.vue'
import { defineComponent } from '@nuxtjs/composition-api'
import 'normalize.css'

export default defineComponent({
  components: {
    // CloudTwitter,
    // CloudWorld,
    ComicTop
  },
  setup() {
    
  },
})
</script>

<template>
  <div>
    <!-- <CloudWorld />
    <CloudTwitter /> -->
    <ComicTop />
  </div>
</template>
